# Local iSCSI Connections

# Connecting to a remote target

In the iSCSI Initiator Application:

1.  In the **Discovery tab**, connect to **Target portals** through the **Discover Portal**
    1.  For a **local** portal, connect to **127.0.0.1**
2.  In the **Targets** tab, **refresh** the **discovered targets** pane
3.  To connect, click on a **target** and click **properties**![](files/01991a87-e8aa-7709-a8c3-b9066eaa61b1/iSCSI_Guide_1.png)
4.  In **properties**, click **add session**
    1.  Check the **Enable multipath** check box
    2.  Click **advanced**
    3.  In Advanced settings under the **general** tab, set the following **connect using** settings:
        
        | Setting Name | Configuration |
        | --- | --- |
        | Local Adapter: | Microsoft iSCSI Initiator |
        | Initiator IP: | Default |
        | Target portal IP: | 127.0.0.1 |
        
    4.  Click **ok** on the **Advanced** settings and the **connect to target** window to add the connection![](files/01991a88-4b62-71fa-9327-7b20e67bfbe6/iSCSI_Guide_Local2.png)
5.  Back in that target’s properties page, verify the target exists.
6.  In properties, add a second connection:
    1.  Click add connection
    2.  Check the Enable multipath check box
    3.  Click advanced
    4.  In Advanced settings under the general tab, set the following connect using settings:
        
        | Setting Name | Configuration |
        | --- | --- |
        | Local Adapter: | Microsoft iSCSI Initiator |
        | Initiator IP: | Default |
        | Target portal IP: | 127.0.0.1 |
        
    5.  Click ok on the Advanced settings and connect to target window to add the connection![](files/01991a88-8ba8-7602-890c-3f7ecb88070a/iSCSI_Guide_Local3.png)
7.  Ensure that there are two connections listed in the Sessions tab of the Properties window.![](files/01991a88-be38-77a9-b378-912811af0ba4/iSCSI_Guide_Local4.png)