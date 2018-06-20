---
title: "How to Cluster the Master Secret Server1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Master Secret server, second node"
  - "Master Secret server, restoring"
  - "clustering, Master Secret server"
  - "Master Secret server, clustering"
ms.assetid: ef817fa4-e43d-4e3d-8686-5bd675708001
caps.latest.revision: 47
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Cluster the Master Secret Server
We recommended that you follow the instructions in this section to cluster the Enterprise Single Sign-On (SSO) service on the master secret server successfully.  
  
 When you cluster the master secret server, the Single Sign-On servers communicate with the active clustered instance of the master secret server. Similarly, the active clustered instance of the master secret server communicates with the SSO database.  
  
 You must be an SSO administrator to perform this procedure.  
  
> [!CAUTION]
>  You cannot install the master secret server on a Network Load Balancing (NLB) cluster.  
  
### To install and configure Enterprise SSO on the cluster nodes  
  
1. Install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on each cluster node. In **Component Installation**, select **Enterprise Single Sign-On Administration Module** and **Enterprise Single Sign-On Master Secret Server**. After installation has completed successfully, do **not** run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration.  
  
2. Create **SSO Administrators** and **SSO Affiliate Administrators** domain groups. To create a clustered instance of the Enterprise SSO service, you must create these groups as domain groups.  
  
3. Create or designate a domain account that is a member of the **SSO Administrators** domain group. The Enterprise SSO service on each node is configured to log on as this domain account. This account must have the **Log on as a service** right on each node in the cluster.  
  
4. Add the account that you are using to log on during the configuration process to the domain **SSO Administrators** group.  
  
   > [!IMPORTANT]
   >  Configuration of the Enterprise SSO service fails if steps 3 and 4 are not completed.  
  
5. Start the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration.  
  
6. Select **Custom Configuration** option and enter the **Database server name**, **User name**, and **Password** values. Select **Configure** to continue.  
  
   > [!NOTE]
   >  Since you are only be configuring the Enterprise SSO service at this time, you can just enter the domain account that you created earlier here.  
  
7. Select the **Enterprise SSO** option from the left pane and set the following options for the Enterprise SSO feature:  
  
   1.  Select the **Enable Enterprise Single Sign-On on this computer** check box.  
  
   2.  Select **Create a new SSO system**.  
  
   3.  Enter the **Data stores** for **Server Name** and **Database Name** values.  
  
   4.  Verify that the domain account that you created earlier is the account that is associated with the Enterprise SSO service.  
  
   5.  Enter the domain SSO Administrators group that you created earlier as the group associated with the SSO Administrator(s) role.  
  
   6.  Enter the domain SSO Affiliate Administrators group that you created earlier as the group associated with the SSO Affiliate Administrator(s) role.  
  
8. Select the **Enterprise SSO Secret Backup** option from the left pane and provide the appropriate parameters for backing up the Enterprise SSO secret. By default, the Enterprise SSO secret is backed up to *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On\\*SSOxxxx*.bak.  
  
9. Click the **Apply Configuration** and review the Summary.  
  
10. Click **Next** to apply the configuration.  
  
11. Click **Finish** to close the Configuration wizard.  
  
12. Close the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration.  
  
13. Log on to the passive cluster node and start the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration.  
  
14. Choose the **Custom Configuration** option and enter the same values for the **Database server name**, **User name**, and **Password** that you entered when configuring the first cluster node. After entering these values, click **Configure** to continue.  
  
15. Select the **Enterprise SSO** option from the left pane and set the following options for the Enterprise SSO feature:  
  
    1.  Select the **Enable Enterprise Single Sign-On on this computer** option.  
  
    2.  Select **Join an existing SSO system**.  
  
    3.  Enter the same values for the SSO Database **Server Name** and **Database Name** that you entered when configuring the first cluster node.  
  
    4.  Enter the same value for the domain account that you entered when configuring the first cluster node.  
  
16. Select **Apply Configuration** to display the Summary.  
  
17. Select **Next** to apply the configuration.  
  
18. Select **Finish** to close the Configuration wizard.  
  
19. Close the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration.  
  
### To update the master secret server name in the SSO database  
  
1.  Type the following commands from a command prompt on the active cluster node to stop and restart the Enterprise SSO service:  
  
    ```  
    net stop entsso  
    ```  
  
     and  
  
    ```  
    net start entsso  
    ```  
  
2.  Change the master secret server name in the SSO database to the cluster name by following these steps:  
  
    > [!NOTE]
    >  The cluster name is the name defined for the network name resource that you have created in the cluster group / clustered service or application that will contain the clustered Enterprise SSO service. For example, the name may be *BIZTALKCLUSTER*.  
  
    1.  Paste the following code in a text editor:  
  
        ```  
        <sso>  
          <globalInfo>  
            <secretServer>BIZTALKCLUSTER</secretServer>  
          </globalInfo>  
        </sso>  
        ```  
  
        > [!NOTE]
        >  *BIZTALKCLUSTER* is a placeholder for the actual network name resource that is created in the cluster group / clustered service or application.  
  
    2.  Save the file as an .xml file. For example, save the file as SSOCLUSTER.xml.  
  
    3.  At a command prompt, change to the Enterprise SSO installation folder. By default, the installation folder is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
    4.  Type the following command at the command prompt to update the master secret server name in the database:  
  
        ```  
        ssomanage -updatedb XMLFile  
        ```  
  
        > [!NOTE]
        >  *XMLFile* is a placeholder for the name of the .xml file that you saved earlier.  
  
### To create the clustered Enterprise SSO resource  
  
1.  If the cluster is not configured with a clustered Distributed Transaction Coordinator (MSDTC) resource then follow the steps in the "Improving Fault Tolerance in BizTalk Server by Using a Windows Server Cluster" white paper at [http://go.microsoft.com/fwlink/?LinkId=69207](http://go.microsoft.com/fwlink/?LinkId=69207) to create a clustered MSDTC resource.  
  
2.  Click **Start**, **Programs**, **Administrative Tools**, and then **Failover Cluster Management** to start the Failover Cluster Management program.  
  
3.  In the left hand pane, right-click **Failover Cluster Management** and click **Manage a Cluster**.  
  
4.  On the **Select a cluster to manage** dialog box, enter the cluster to be managed and click **OK**.  
  
5.  In the left hand pane click to select a clustered service or application that contains an IP Address and Network Name resource. Follow the steps in [How to Create a Cluster Group with a Disk, IP Address, and Name Resource](../core/how-to-create-a-cluster-group-with-a-disk-ip-address-and-name-resource1.md) to create a group with an IP Address and Network Name resource if one does not already exist.  
  
    > [!NOTE]
    >  A clustered Enterprise SSO service does not explicitly require the use of a clustered Physical Disk resource in the same group.  
  
6.  Right-click the clustered service or application, point to **Add a resource**, and click **Generic Service** to display the **New Resource Wizard** dialog.  
  
    > [!IMPORTANT]
    >  In the **Generic Service Parameters** dialog box, if you do not click to select the **Use Network Name for computer name** check box, SSO client computers will generate an error similar to the following when they try to contact this clustered instance of the Enterprise SSO service:  
    >   
    >  Failed to retrieve master secrets.  
    >   
    >  Verify that the master secret server name is correct and that it is available. Secret Server Name: ENTSSO Error Code: 0x800706D9, there are no more endpoints available from the endpoint mapper.  
  
7.  On the **Select Service** page of the **New Resource Wizard**, click to select **Enterprise Single Sign-On Service** and click **Next**.  
  
8.  On the **Confirmation** page click **Next**.  
  
9. On the **Summary** page click **Finish**. A clustered instance of the Enterprise Single Sign-On Service will appear under **Other Resources** in the center pane of the **Failover Cluster Management** interface.  
  
10. Right-click the clustered instance of the Enterprise Single Sign-On Service and select **Properties** to display the **Enterprise Single Sign-On Service Properties** dialog box.  
  
11. Click the **Dependencies** tab of the properties dialog box and click **Insert**.  
  
12. Click the drop down box under **Resource**, select the **Name:** resource and click **OK**.  
  
### To restore the master secret on the second cluster node  
  
1.  In Failover Cluster Management, right click the clustered service or application that contains the clustered Enterprise Single Sign-On service and then click **Bring this service or application online** to start all of the resources in the clustered service or application.  
  
2.  Right-click the clustered service or application, point to **Move this service or application to another node**, and click the second node. This step moves the clustered service or application that contains the clustered Enterprise Single Sign-On service from the first node to the second node.  
  
3.  Right-click the clustered Enterprise Single Sign-On service and click **Take this service or application offline**, then right-click the clustered instance of the Enterprise SSO service and click **Bring this service or application online**.  
  
    > [!NOTE]
    >  If this step is not completed the attempt to restore the master secret may not succeed.  
  
4.  Copy the master secret backup file from the first node to the \Enterprise Single Sign-On installation folder on the second node. By default, the installation folder is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
5.  Log on to the second node and at a command prompt, change to the Enterprise SSO installation folder.  
  
6.  Type the following command from the command prompt to restore the master secret to the second node:  
  
    ```  
    ssoconfig -restoresecret RestoreFile  
    ```  
  
    > [!NOTE]
    >  Replace *RestoreFile* with the path of and the name of the backup file that contains the master secret.  
  
     The master secret is stored in the registry at the following location:  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS  
  
7.  Move the clustered service or application that contains the clustered Enterprise Single Sign-On service from this cluster node to other cluster node to ensure failover functionality. Then move the cluster group back to verify fail-back functionality.  
  
## See Also  
 [How to Create a Cluster Group with a Disk, IP Address, and Name Resource](../core/how-to-create-a-cluster-group-with-a-disk-ip-address-and-name-resource1.md)
