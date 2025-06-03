---
description: "Learn more about: How to Move the Master Secret Server"
title: "How to Move the Master Secret Server"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Move the Master Secret Server
This topic documents the steps you can follow to move the master secret from one server to another and the steps you can follow to move the master secret from one server to a Windows Server Cluster.  
  
### To move the master secret from one server to another server  
  
1.  Install Microsoft Enterprise Single Sign-On (SSO) Server on the new master secret server if it is not already installed. Launch Microsoft Enterprise Single Sign-On Server setup from \Platform\SSO\setup.exe on the BizTalk Server CD.  
  
2.  Configure Enterprise SSO on the new master secret server if it is not already configured. Follow these steps to configure Enterprise SSO:  
  
    1.  Open the Configuration tool. By default, the configuration tool is located at \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On\Configuration.exe.  
  
    2.  Click to select **Enterprise SSO** in the left pane.  
  
    3.  Select the check box next to **Enable Enterprise Single Sign-On on this computer** in the right pane.  
  
    4.  Click the option to **Join an existing SSO System**.  
  
    5.  Specify the existing **Server Name** and **Database Name** for the SSO database options.  
  
    6.  Specify the existing Enterprise SSO service account for the **Enterprise Single Sign-On Server for the Windows Service** option.  
  
        > [!NOTE]
        >  This must be a domain account.  
  
    7.  Click the option to **Apply Configuration** and click **Configure** in the Configuration Wizard dialog box to complete the configuration.  
  
    8.  Click **Finish** and close the Configuration tool.  
  
3.  Back up the existing master secret following the steps in [How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md).  
  
4.  Change the master secret server name in the SSO database to reference the new master secret server. For example, the name of the new master secret server may be **NewMSSServer**. To do this, follow these steps on the original master secret server:  
  
    1.  Paste the following code in a text editor such as notepad.exe:  
  
        ```  
        <sso>  
        <globalInfo>  
        <secretServer>NewMSSServer</secretServer>  
        </globalInfo>  
        </sso>  
        ```  
  
    2.  Save the file as .xml file. For example, save the file as **NewMSSServer.xml**.  
  
    3.  At a command prompt, change to the Enterprise SSO installation folder. By default, the installation folder is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
    4.  Type **ssomanage -updatedb** *XMLFile* to update the master secret server name in the database.  
  
        > [!NOTE]
        >  Replace *XMLFile* with the name of the .xml file that you saved.  
  
        > [!NOTE]
        >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
5.  Restart the Enterprise Single Sign-On service on the new master secret server.  
  
6.  Restore the backed-up master secret onto the new master secret server by following the steps in [How to Restore the Master Secret](../core/how-to-restore-the-master-secret.md) on the new master secret server.  
  
### To move the master secret from one server to a Windows Server Cluster  
  
1.  Install and configure the Enterprise SSO service on a Windows Server cluster by following the steps in [How to Cluster the Master Secret Server](../core/how-to-cluster-the-master-secret-server1.md). Complete all of the steps in this topic except for the steps described in the **Restore the master secret on the second cluster node** section. Since you will be moving the existing master secret server to the cluster do not choose the option to **Create a new SSO system** when configuring Enterprise SSO on the cluster nodes. When configuring each cluster node, set the following options for the Enterprise SSO feature in the BizTalk Server Configuration program:  
  
    1.  Check the box next to **Enable Enterprise Single Sign-On on this computer**.  
  
    2.  Click the option to **Join an existing SSO system**.  
  
    3.  Enter values for the existing SSO Database Server Name and Database Name.  
  
    4.  Enter the existing SSO Service account when specifying the account to use for the Enterprise Single Sign-On Service.  
  
2.  Copy the existing master secret backup file to the \Enterprise Single Sign-On folder on each cluster node.  
  
3.  If this Windows Server Cluster will host one or more clustered BizTalk hosts, set the SSO Server name for all users to the clustered master secret server with the ssomanage command line utility. This command should be run from the Enterprise SSO installation folder on each BizTalk Server in the group. For example, the following command line will set the SSO Server name for all users to the clustered master secret server:  
  
    ```  
    ssomanage -serverall SSOCLUSTER  
    ```  
  
    > [!NOTE]
    >  *SSOCLUSTER* is a placeholder for the actual network name resource that is created in the cluster group that contains the clustered master secret server resourceIn this scenario, all BizTalk hosts must be created as cluster resources in the same cluster group as the clustered Enterprise SSO service resource. Running a non-clustered BizTalk host instance on a Windows Server Cluster node where the Enterprise SSO service is clustered is not a supported configuration. This is because the non-clustered BizTalk host instance will fail when the clustered Enterprise SSO service is failed over to another node due to the dependency of a BizTalk host instance on the SSO service.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
4.  In Cluster Administrator, right-click the cluster group that contains the clustered Enterprise SSO service resource, and click **Bring Online** to start all of the resources in the cluster group.  
  
5.  If this Windows Server Cluster will host one or more clustered BizTalk hosts, update the SSO Server name accessible in the **BizTalk Group Properties** page to reference the clustered master secret server. Launch **BizTalk Server Administration**, right-click the BizTalk Group and select the **Properties** menu item, then update the entry for **SSO Server name** and click **OK**.  
  
    > [!NOTE]
    >  In this scenario, all BizTalk hosts must be created as cluster resources in the same cluster group as the clustered Enterprise SSO service resource. Running a non-clustered BizTalk host instance on a Windows Server Cluster node where the Enterprise SSO service is clustered is not a supported configuration. This is because the non-clustered BizTalk host instance will fail when the clustered Enterprise SSO service is failed over to another node due to the dependency of a BizTalk host instance on the SSO service.  
  
6.  Right-click the clustered instance of the Enterprise SSO service and click **Take Offline**, then right-click the clustered instance of the Enterprise SSO service and click **Bring Online**.  
  
    > [!NOTE]
    >  If this step is not completed, attempts to restore the master secret may not succeed.  
  
7.  Restore the backed-up master secret on each node of the Windows cluster that houses the clustered master secret server. Follow the steps in [How to Restore the Master Secret](../core/how-to-restore-the-master-secret.md) on each node of the Windows cluster that houses the clustered master secret server.  
  
## See Also  
 [Managing the Master Secret](../core/managing-the-master-secret.md)
