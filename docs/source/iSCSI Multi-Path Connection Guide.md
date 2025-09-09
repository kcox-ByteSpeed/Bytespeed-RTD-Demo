# iSCSI Multi-Path Connection Guide

# Connecting to a local target

In the **iSCSI Initiator** Application:

1.  In the **Discovery** tab, connect to **Target portals** through the **Discover Portal**
    1.  For a local portal, connect to **127.0.0.1**
2.  In the **Targets tab, refresh** the **discovered targets** pane
3.  To connect, click on a **target** and click **properties**![](files/01991a64-a0de-706c-88be-e2c5af02ac4e/iSCSI_Guide_1.png)
4.  In properties, click add session
    1.  Check the **Enable multipath** check box
    2.  Click **advanced**
    3.  In **Advanced** settings under the general tab, set the following **connect using** settings:
        
        | Setting Name | Configuration |
        | --- | --- |
        | Local Adapter: | Microsoft iSCSI Initiator |
        | Initiator IP: | Default |
        | Target portal IP: | 127.0.0.1 |
        
    4.  Click **ok** on the **Advanced settings** and **connect to target** window to add the connection![](files/01991a68-d639-7032-8c93-076ff255190f/iSCSI_Guide_Local2.png)
5.  Back in that target’s properties page, verify the target exists.
6.  In properties, add a second connection:
    1.  Click add connection
    2.  Check the **Enable multipath** check box
    3.  Click **advanced**
    4.  In **Advanced** settings under the general tab, set the following **connect using** settings:
    5.  Click **ok** on the **Advanced settings** and **connect to target** window to add the connection
        
        | Setting Name | Configuration |
        | --- | --- |
        | Local Adapter: | Microsoft iSCSI Initiator |
        | Initiator IP: | Default |
        | Target portal IP: | 127.0.0.1 |
        
        ![](files/01991a6d-faa2-77d4-9e27-7ecf09aba478/iSCSI_Guide_Local3.png)
7.  Ensure that there are **two connections** listed in the **Sessions** tab of the **Properties** window.![](files/01991a70-52e7-7115-8727-c5a058c91524/iSCSI_Guide_Local4.png)

# Connecting to a remote target

In the **iSCSI Initiator** Application:

1.  In the **Discovery** tab, connect to **Target portals** through the **Discover Portal**
    1.  For remote portals, connect to **iSCSI1/Data1 and iSCSI2/Data2**
2.  In the **Targets tab, refresh** the **discovered targets** pane
3.  To connect, click on a **target** and click **properties**
4.  In properties, click add session
    1.  Check the **Enable multipath** check box
    2.  Click **advanced**
    3.  In **Advanced** settings under the general tab, set the following **connect using** settings:
        
        :::success
        Connect using **iSCSI1 / Data1**
        
        - Below is an example of connecting to a target on H2 from H1
        :::
        
        | Setting Name | Configuration |
        | --- | --- |
        | Local Adapter: | Microsoft iSCSI Initiator |
        | Initiator IP: | 172.16.21.5 |
        | Target portal IP: | 172.16.21.6 / 3260 |
        
    4.  Click **ok** on the **Advanced settings** and **connect to target** window to add the connection![](files/01991a73-e434-7132-b21c-eb14a5395d6c/iSCSI_Guide_Remote1.png)
5.  Back in that target’s properties page, verify the target exists.
6.  In properties, add a second connection:
    1.  Click add connection
    2.  Check the **Enable multipath** check box
    3.  Click **advanced**
    4.  In **Advanced** settings under the general tab, set the following **connect using** settings:
    5.  Click **ok** on the **Advanced settings** and **connect to target** window to add the connection
        
        :::success
        Connect using **iSCSI2 / Data2**
        
        - Below is an example of connecting to a target on H2 from H1
        :::
        
        | Setting Name | Configuration |
        | --- | --- |
        | Local Adapter: | Microsoft iSCSI Initiator |
        | Initiator IP: | 172.16.22.5 |
        | Target portal IP: | 172.16.22.6 |
        
        ![](files/01991a75-8bf9-714d-ba73-ada08d06a68d/iSCSI_Guide_Remote2.png)
7.  Ensure that there are **two connections** listed in the **Sessions** tab of the **Properties** window.![](files/01991a77-21c3-742e-8dc8-1bee31fa5941/iSCSI_Guide_Remote3.png)