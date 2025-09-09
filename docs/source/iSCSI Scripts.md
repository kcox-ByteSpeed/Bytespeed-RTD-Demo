# iSCSI Scripts

# Prerequisites

- iSCSI and MPIO are installed and running.

- For most of these scripts to work, you need JSON mapping out nodes and IP information. It will look for this structure:

```json
{
"nodes": [
    {
    "name": "HVH1",
    "MGMT": "10.21.25.51",
    "OOBM": "10.64.2.25",
    "Sync1": "172.16.25.1",
    "Data1": "172.16.26.1",
    "Data2": "172.16.27.1",
    "Sync2": "172.16.28.1"
    },
    {
    "name": "HVH2",
    "MGMT": "10.21.25.52",
    "OOBM": "10.64.2.26",
    "Sync1": "172.16.25.2",
    "Data1": "172.16.26.2",
    "Data2": "172.16.27.2",
    "Sync2": "172.16.28.2"
    }
]
}
```

---

# Script to generate JSON (not tested extensively)

```powershell
# Prompt for credentials to use for all remote sessions
$cred = Get-Credential

# List of remote computers
$computers = @("H1", "H2")

# Script block to run on each remote computer
$scriptBlock = {
    $hostname = $env:COMPUTERNAME

    # Map keywords in adapter names to role names
    $roleMap = @{
        "mgmt" = "MGMT"; "oobm" = "OOBM"; "sync1" = "Sync1"
        "sync2" = "Sync2"; "data1" = "Data1"; "data2" = "Data2"
    }

    # Store hostname and matched IPs
    $result = @{ name = $hostname }

    # Get non-APIPA IPv4 addresses and normalize adapter names
    $adapters = Get-NetIPAddress -AddressFamily IPv4 -PrefixOrigin Manual | Where-Object {
        $_.IPAddress -notlike '169.254*'
    } | ForEach-Object {
        $name = (Get-NetAdapter -InterfaceIndex $_.InterfaceIndex).Name
        [PSCustomObject]@{
            Name = $name
            Normalized = ($name -replace '\s', '').ToLower()
            IP = $_.IPAddress
        }
    }

    # Match normalized names to roles
    foreach ($a in $adapters) {
        foreach ($k in $roleMap.Keys) {
            if ($a.Normalized -like "*$k*") {
                $result[$roleMap[$k]] = $a.IP
            }
        }
    }

    return $result
}

# Run the script block on all computers and collect results
$nodes = Invoke-Command -ComputerName $computers -Credential $cred -ScriptBlock $scriptBlock

# Build final JSON object with all node data
$json = @{ nodes = $nodes } | ConvertTo-Json -Depth 3

# Output JSON string
Write-Output $json

# Parse the JSON
$json = $json | ConvertFrom-Json
$json
```

---

# Add discovery IPs

The following script adds discovery IPs for each node in the StarWind Cluster

```powershell
# JSON data as a string (could also come from a file)
# Ensure json gets parsed $json = $json | ConvertFrom-Json

# Get current computer name (matches 'name' field in JSON)
$currentNode = $env:COMPUTERNAME.ToUpper()

# Build list of discovery IPs
$discoveryIPs = @()

foreach ($node in $json.nodes) {
    if ($node.name -eq $currentNode) {
        $discoveryIPs += "127.0.0.1"
    } else {
        $discoveryIPs += $node.Data1
        $discoveryIPs += $node.Data2
    }
}

# Add discovery portals
foreach ($ip in $discoveryIPs | Sort-Object -Unique) {
    try {
        New-IscsiTargetPortal -TargetPortalAddress $ip -ErrorAction Stop | Out-Null
        Write-Host "Added portal: $ip"
    } catch {
        Write-Warning "Failed to add portal IP: $ip"
    }
}
```

---

# Connect targets

Connects targets:

- Remote targets are connected via Data1 and Data2 networks
- Local targets are connected via 2 loopback connections (performance)

```powershell
$currentNode = $env:COMPUTERNAME.ToLower()
$localNodeJson = $json.nodes | where-object { $_.name.tolower() -eq $currentNode.tolower()}

$targetSourceIPMap = @($localNodeJson.Data1, $localNodeJson.Data2)

$targets = Get-IscsiTarget

foreach ($target in $targets) {

    # Find node by matching NodeAddress against either name or MGMT IP
    $node = $json.nodes | Where-Object {
        $nodeNameMatch = $target.NodeAddress.ToLower().Contains($_.name.ToLower())
        $ipMatch = $target.NodeAddress.Contains($_.MGMT)
        $nodeNameMatch -or $ipMatch
    }

    if (-not $node) {
        Write-Warning "No node found matching target $($target.NodeAddress)"
        continue
    }

    # Assuming $node is a single object, not array
    $node = $node | Select-Object -First 1

    if ($node.name.ToLower() -eq $currentNode) {
        # Local node: connect twice to 127.0.0.1
        1..2 | ForEach-Object {
            Connect-IscsiTarget -NodeAddress $target.NodeAddress `
                                -TargetPortalAddress "127.0.0.1" `
                                -IsMultipathEnabled $true `
                                -IsPersistent $true | Out-Null
            Write-Host "Connected $($target.NodeAddress) on 127.0.0.1 (instance $_)"
        }
    } else {
        # Remote node: connect to Data1 and Data2 IPs
        @($node.Data1, $node.Data2) | ForEach-Object -Begin { $i=0 } -Process {
            $ip = $_
            $source = $targetSourceIPMap[$i]

            Connect-IscsiTarget -NodeAddress $target.NodeAddress `
                                -TargetPortalAddress $ip `
                                -InitiatorPortalAddress $source `
                                -IsMultipathEnabled $true `
                                -IsPersistent $true | Out-Null

            Write-Host "Connected $($target.NodeAddress) on $ip via $source"

            $i++
        }
    }
}
```

---

# Miscellaneous Scripts/Commands

## Remove All Variables

```powershell
Remove-Variable * -ErrorAction SilentlyContinue
```

---

## Reset iSCSI Config

```powershell
 # Unregister persistent sessions
Get-IscsiSession | Where-Object { $_.IsPersistent } | ForEach-Object {
    Unregister-IscsiSession -SessionIdentifier $_.SessionIdentifier
}

# Disconnect all active sessions
Get-IscsiSession | ForEach-Object {
    Disconnect-IscsiTarget -NodeAddress $_.TargetNodeAddress -Confirm:$false
}

# Remove all target portals
Get-IscsiTargetPortal | ForEach-Object {
    Remove-IscsiTargetPortal -TargetPortalAddress $_.TargetPortalAddress -Confirm:$false
}

# Restart the iSCSI service to clean everything up
Restart-Service -Name MSiSCSI -Force
```

---

## Remove Favorite Targets

:::warning
Requires the sessions to be connected still
:::

```powershell
get-iscsisession | Where-Object { $_.IsPersistent } | ForEach-Object { 
    Unregister-IscsiSession -SessionIdentifier $_.SessionIdentifier 
}
```

---

## Disconnect All Active iSCSI Sessions

```powershell
Get-IscsiSession | ForEach-Object {
    Disconnect-IscsiTarget -NodeAddress $_.TargetNodeAddress -Confirm:$false
}
```

---

## Remove Target Portals

```powershell
 Get-IscsiTargetPortal | ForEach-Object { 
    Remove-IscsiTargetPortal -TargetPortalAddress $_.TargetPortalAddress -Confirm:$false 
    }
```

---

## Restart iSCSI Service

```powershell
 Restart-Service -Name MSiSCSI -Force
```