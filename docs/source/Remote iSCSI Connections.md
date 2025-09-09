# Remote iSCSI Connections

# Connecting to a remote target

In the iSCSI Initiator Application:

1.  In the **Discovery tab**, connect to **Target portals** through the **Discover Portal**
    1.  For a **remote** portal, connect to **both iSCSI1 / Data1 and iSCSI2 / Data2**
2.  In the **Targets** tab, **refresh** the **discovered targets** pane
3.  To connect, click on a **target** and click **properties**
4.  In **properties**, click **add session**
    1.  Check the **Enable multipath** check box
    2.  Click **advanced**
    3.  In Advanced settings under the **general** tab, set the following **connect using** settings:
        
        :::success
        Connect using **iSCSI1 / Data1**
        
        - The following is an example of connecting to a Storage Device on H2 from H1
        :::
        
        | Setting Name | Configuration |
        | --- | --- |
        | Local Adapter: | Microsoft iSCSI Initiator |
        | Initiator IP: | &lt;Data1 on H1&gt; |
        | Target portal IP: | &lt;Data1 on H2&gt; / 3260 |
        
    4.  Click **ok** on the **Advanced** settings and the **connect to target** window to add the connection![](files/01991a89-a36c-76d1-b332-70b2d3288e11/iSCSI_Guide_Remote1.png)
5.  Back in that target’s properties page, verify the target exists.
6.  In properties, add a second connection:
    1.  Click add connection
    2.  Check the Enable multipath check box
    3.  Click advanced
    4.  In Advanced settings under the general tab, set the following connect using settings:
        
        :::success
        Connect using **iSCSI2 / Data2**
        
        - The following is an example of connecting to a Storage Device on H2 from H1
        :::
        
        | Setting Name | Configuration |
        | --- | --- |
        | Local Adapter: | Microsoft iSCSI Initiator |
        | Initiator IP: | &lt;Data2 on H1&gt; |
        | Target portal IP: | &lt;Data2 on H2&gt; / 3260 |
        
    5.  Click ok on the Advanced settings and connect to target window to add the connection![](files/01991a89-e557-7794-a60c-0a1fa84f2179/iSCSI_Guide_Remote2.png)
7.  Ensure that there are two connections listed in the Sessions tab of the Properties window.![](files/01991a8a-147f-765c-b66c-8671c46e4dcc/iSCSI_Guide_Remote3.png)