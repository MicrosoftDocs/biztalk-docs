---
title: "How to Cluster SSO and a BizTalk Host in the Same Cluster Group1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 413cc8f4-f343-4c1c-8b79-3b15cb4c101d
caps.latest.revision: 44
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Cluster SSO and a BizTalk Host in the Same Cluster Group
With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] you can cluster one or more BizTalk hosts and the Enterprise Single Sign-On (SSO) service on the same Windows Server cluster.  
  
> [!NOTE]
>  Correct implementation of this strategy requires that you create any BizTalk host instances and the SSO service as cluster resources in the same cluster group.  
  
 The use of Windows Clustering with one or more BizTalk hosts and SSO typically falls into one of these categories:  
  
1. Clustering the SSO master secret server and one or more BizTalk hosts in the same cluster group.  
  
    In this scenario, the dependency between the clustered BizTalk hosts and the clustered SSO service is maintained so that if the cluster group is failed over, all resources move with the group.  
  
    If the SSO service is configured as a clustered resource on a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer, you must create a clustered IIS web service in the same cluster group. This must be done to ensure that all isolated host instances will run on the cluster node that the SSO service is running on. This ensures that any adapters that run in an isolated host instance will have access to the SSO service since isolated host instances run in IIS.  
  
   > [!NOTE]
   >  If an unclustered instance of a BizTalk host is running on the same cluster node that a clustered instance of the SSO service is running, the clustered instance of the SSO service cannot be failed over unless the unclustered instance of the BizTalk host is stopped. An unclustered instance of the BizTalk host maintains a dependency upon the clustered instance of the SSO service running on the cluster node and prevents the clustered instance of the SSO service from failing over. For this reason, it is recommended that you do not create an unclustered instance of a BizTalk host to run on the same cluster node that is running a clustered instance of the SSO service.  
  
2. Clustering the SSO service (non master secret server) and one or more BizTalk hosts in the same cluster group. This scenario requires that a remote master secret server be available. In this scenario, the dependency between the clustered BizTalk hosts and the clustered SSO service is maintained so if the cluster group is failed over, all resources move with the group.  
  
    If the SSO service is configured as a clustered resource on a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer, you must create a clustered IIS web service in the same cluster group. This must be done to ensure that all isolated host instances will run on the cluster node that the SSO service is running on. This ensures that any adapters that run in an isolated host instance will have access to the SSO service since isolated host instances run in IIS.  
  
   > [!NOTE]
   >  If an unclustered instance of a BizTalk host is running on the same cluster node that a clustered instance of the SSO service is running then the clustered instance of the SSO service cannot be failed over unless the unclustered instance of the BizTalk host is stopped. An un-clustered instance of the BizTalk host maintains a dependency upon the clustered instance of the SSO service running on the cluster node and prevents the clustered instance of the SSO service from failing over. For this reason, it is recommended that you not create a unclustered instance of a BizTalk host to run on the same cluster node that is running a clustered instance of the SSO service.  
  
3. Clustering one or more BizTalk hosts on a Windows Server cluster without clustering the SSO service. In this scenario, one or more BizTalk hosts are configured as cluster resources but the SSO service is not configured as a clustered resource. This design provides high availability for the clustered BizTalk hosts but does not provide high availability for the SSO service. In this scenario, if the SSO service on a node fails then BizTalk Server components that depend on SSO on that node will also fail. For more information about how to configure a BizTalk Server host as a cluster resource see [How to Configure a BizTalk Host as a Cluster Resource](http://msdn.microsoft.com/library/6e9aab00-7623-4175-bb12-ba916306f1e3).  
  
   The following procedures describe the steps that you should follow to cluster a BizTalk host and the SSO service on the same Windows Server cluster.  
  
### To cluster a BizTalk host and the SSO master secret server on the same Windows Server cluster  
  
1. If the cluster is not configured with a clustered Distributed Transaction Coordinator (MSDTC) resource, cluster MSDTC on a Windows Server failover cluster by following the steps in [Checklist: Creating an MS DTC Resource in a Windows Server 2008 Failover Cluster](http://go.microsoft.com/fwlink/p/?LinkID=129677) (http://go.microsoft.com/fwlink/p/?LinkID=129677).  
  
2. Install and configure the SSO service on the Windows Server cluster by following the steps in [How to Cluster the Master Secret Server](http://msdn.microsoft.com/library/59895616-4178-46d0-b9ff-95589b809ff5). Since you will be running BizTalk Server on the Windows Server cluster, install all required BizTalk Server components even though you will only be configuring the SSO components at this time.  
  
3. Cluster IIS on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer by following the steps documented in [Microsoft Knowledge Base article 970759 "Configuring IIS 7.0 in a Microsoft Windows Server 2008 failover cluster"](http://go.microsoft.com/fwlink/p/?LinkId=152793) (<http://go.microsoft.com/fwlink/p/?LinkId=152793>). Create the clustered IIS Web service in the same cluster group as the clustered SSO service.  
  
4. Move the cluster group that contains the clustered SSO service to one of the cluster nodes, and log on to this cluster node.  
  
5. Start the BizTalk Server Configuration program, and complete the configuration of BizTalk Server on this cluster node. Since this is the first BizTalk Server computer in the group, click **Create a new BizTalk Group** when configuring the BizTalk Group.  
  
6. Once the BizTalk Server configuration has completed successfully, move the cluster group that contains the clustered SSO service to the other cluster node, and log on to this cluster node.  
  
7. Start the BizTalk Server Configuration program, and complete the configuration of BizTalk Server on this cluster node. Click **Join an existing BizTalk Group** when configuring the BizTalk Group component on this cluster node, and specify the BizTalk group that you created on the first node.  
  
8. Once the BizTalk Server configuration has completed successfully, create one or more clustered BizTalk hosts by following the steps in [How to Configure a BizTalk Host as a Cluster Resource](http://msdn.microsoft.com/library/6e9aab00-7623-4175-bb12-ba916306f1e3).  
  
   > [!NOTE]
   >  In this scenario, all BizTalk hosts must be created as cluster resources in the same cluster group as the clustered SSO service resource. Running a unclustered BizTalk host instance on a Windows Server Cluster node where the SSO service is clustered is not a supported configuration. This is because the unclustered BizTalk host instance will fail when the clustered SSO service is failed over to another node due to the dependency of a BizTalk host instance on the SSO service.  
  
### To cluster a BizTalk host and SSO (non master secret server) on the same Windows Server cluster when the SSO master secret server is remote  
  
1. If the cluster is not configured with a clustered Distributed Transaction Coordinator (MSDTC) resource, cluster MSDTC on a Windows Server failover cluster by following the steps in [Checklist: Creating an MS DTC Resource in a Windows Server 2008 Failover Cluster](http://go.microsoft.com/fwlink/p/?LinkID=129677) (http://go.microsoft.com/fwlink/p/?LinkID=129677).  
  
2. Create domain groups with the names **SSO Administrators** and **SSO Affiliate Administrators**. To create a clustered instance of the SSO service, you must create the **SSO Administrators** and **SSO Affiliate Administrators** groups as domain groups.  
  
3. Create or designate a domain account that is a member of the **SSO Administrators** domain group. The SSO service on each node will be configured to log on as this domain account. This account must have the **Log on as a service** right on each node in the cluster.  
  
4. Add the account that you are using to log on during the installation and configuration process to the domain **SSO Administrators** group.  
  
   > [!IMPORTANT]
   >  Configuration of the SSO service will fail if steps 3 and 4 are not completed.  
  
5. Log on to one of the cluster nodes and install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Select the option to start the configuration program when installation has completed successfully.  
  
6. Choose the **Custom Configuration** option and enter the appropriate values for the **Database server name**, **User name** and **Password** fields. After entering these values click the **Configure** button to continue.  
  
7. Set the following options for the SSO feature:  
  
   1.  Select the check the box next to **Enable Enterprise Single Sign-On on this computer**.  
  
   2.  Click the option to **Join an existing SSO system**.  
  
   3.  Enter values for the existing SSO Database Server Name and Database Name.  
  
   4.  Enter the existing SSO service account when specifying the account to use for the Enterprise Single Sign-On service.  
  
8. Since this is the first BizTalk Server in the group choose the option to **Create a new BizTalk Group** when configuring the BizTalk Group component.  
  
9. Specify the remaining configuration options as needed and apply the BizTalk Server configuration to this node.  
  
10. Once the BizTalk Server configuration has completed successfully on the first node, log on to the second node and install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Select the option to start the configuration program when installation has completed successfully.  
  
11. Choose the **Custom Configuration** option, and then enter the appropriate values for the **Database server name**, **User name** and **Password** fields. After entering these values, click the **Configure** button to continue.  
  
12. Set the following options for the SSO feature:  
  
    1.  Select the check the box next to **Enable Enterprise Single Sign-On on this computer**.  
  
    2.  Click **Join an existing SSO system**.  
  
    3.  Enter values for the existing SSO Database Server Name and Database Name.  
  
    4.  Enter the existing SSO service account when specifying the account to use for the Enterprise Single Sign-On service.  
  
13. Choose the option to **Join an existing BizTalk Group** when configuring the BizTalk Group component on this cluster node, and specify the BizTalk group that you created on the first node.  
  
14. Specify the remaining configuration options as needed and apply the BizTalk Server configuration to this node.  
  
15. After the BizTalk Server configuration has completed successfully, follow these steps to cluster the SSO service:  
  
    1.  Stop the SSO service on each of the cluster nodes by typing the following command from a command:  
  
        ```  
        net stop entsso  
        ```  
  
    2.  In Failover Cluster Management, move all cluster groups to one node and log on to this node.  
  
    3.  In the left hand pane click to select a clustered service or application that contains an IP Address and Network Name resource. This clustered service or application will contain the clustered SSO service and the clustered BizTalk host.  
  
        > [!NOTE]
        >  A clustered SSO service does not explicitly require the use of a clustered Physical Disk resource in the same group.  
  
    4.  Right-click the clustered service or application, point to **Add a resource**, and click **Generic Service** to display the **New Resource Wizard** dialog box.  
  
    5.  On the **Select Service** page of the **New Resource Wizard**, select **Enterprise Single Sign-On Service**, and then click **Next**.  
  
    6.  On the **Confirmation** page click **Next**.  
  
    7.  On the **Summary** page click **Finish**. A clustered instance of the Enterprise Single Sign-On Service will appear under **Other Resources** in the center pane of the **Failover Cluster Management** interface.  
  
    8.  Right-click the clustered instance of the Enterprise Single Sign-On Service and select **Properties** to display the **Enterprise Single Sign-On Service Properties** dialog box.  
  
    9. Click the **Dependencies** tab of the properties dialog box and click **Insert**.  
  
    10. Click the drop down box under **Resource**, select the **Name:** resource and click **OK**.  
  
        > [!IMPORTANT]
        >  If you do not add the dependency to the **Name:** resource, SSO client computers will generate an error similar to the following when they try to contact this clustered instance of the SSO service:  
        >   
        >  Failed to retrieve master secrets.  
        >   
        >  Verify that the master secret server name is correct and that it is available. Secret Server Name: ENTSSO Error Code: 0x800706D9, there are no more endpoints available from the endpoint mapper.  
  
16. Cluster IIS on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer by following the steps documented in [Microsoft Knowledge Base article 970759 "Configuring IIS 7.0 in a Microsoft Windows Server 2008 failover cluster"](http://go.microsoft.com/fwlink/p/?LinkId=152793) (<http://go.microsoft.com/fwlink/p/?LinkId=152793>). Create the clustered IIS web service in the same cluster group as the clustered SSO service.  
  
17. In Failover Cluster Management, right click the clustered service or application that contains the clustered Enterprise Single Sign-On service and then click **Bring this service or application online** to start all of the resources in the clustered service or application.  
  
18. Right-click the clustered service or application, point to **Move this service or application to another node**, and click the second node. This step moves the clustered service or application that contains the clustered Enterprise Single Sign-On service from the first node to the second node.  
  
19. Right-click the clustered Enterprise Single Sign-On service and click **Take this service or application offline**, then right-click the clustered instance of the SSO service and click **Bring this service or application online**.  
  
20. Set the SSO server name for all users to the clustered SSO service with the ssomanage command line utility. This command should be run from the SSO installation folder on each BizTalk server in the group. For example, the following command line will set the SSO server name for all users to the clustered SSO service:  
  
    ```  
    ssomanage -serverall SSOCLUSTER  
    ```  
  
    > [!NOTE]
    >  *SSOCLUSTER* is a placeholder for the actual network name resource that is created in the cluster group that contains the clustered SSO service.  
  
21. Update the SSO Server name accessible in the **BizTalk Group Properties** page to reference the clustered SSO service. Open **BizTalk Server Administration**, right-click the BizTalk Group, select the **Properties** menu item, update the entry for SSO Server name, and then click **OK**.  
  
22. Follow the steps in [How to Configure a BizTalk Host as a Cluster Resource](http://msdn.microsoft.com/library/6e9aab00-7623-4175-bb12-ba916306f1e3) to create one or more clustered BizTalk host instances in the same cluster group that you have created the clustered SSO service.  
  
    > [!NOTE]
    >  In this scenario, all BizTalk hosts must be created as cluster resources in the same cluster group as the clustered SSO service resource. Running an unclustered BizTalk host instance on a Windows Server Cluster node where the SSO service is clustered is not a supported configuration. This is because the unclustered BizTalk host instance will fail when the clustered SSO service is failed over to another node due to the dependency of a BizTalk host instance on the SSO service.