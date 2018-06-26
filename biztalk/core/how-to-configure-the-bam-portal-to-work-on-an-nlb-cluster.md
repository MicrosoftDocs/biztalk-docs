---
title: "How to Configure the BAM Portal to Work on an NLB Cluster | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96c04fde-dc12-42fb-9193-aa74819fe880
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the BAM Portal to Work on an NLB Cluster
The BAM portal can be configured to work in a network load balancing (NLB) cluster.  
  
> [!IMPORTANT]
>  BAM Portal *only* runs in 32-bit mode. If IIS is installed on a 64-bit machine, then confirm ASP.NET 2.0 is enabled in 32-bit mode. To do this, open IIS Manager, open **Application Pool**, select the application pool (BAMAppPool), and then click **Advanced Settings**. In **Enable 32-bit applications**, select **True**.  
>   
>  For additional BAM Portal requirements, see [Planning for the BAM Portal](../core/planning-for-the-bam-portal.md).  
  
### To prepare to configure BAM portal on an NLB cluster  
  
1.  Install and configure the portal on the first computer.  
  
    > [!NOTE]
    >  You only configure the portal on the first computer. You have the option of enabling the BAM portal on other the other computers in the cluster, but the configuration is done only on the first computer.  
  
2.  Install the portal components on all the computers to be included in the NLB cluster, and then join the other computers in the cluster to the BizTalk group of the computer on which the portal is configured. You must enable the BizTalk groups and join the appropriate group.  
  
3.  Select the BizTalk Management database configured for the computer on which the portal is installed.  
  
4.  Create the NLB cluster. For more information about how to create and manage network load balancing clusters, see "Create and Manage Network Load Balancing Clusters" at [http://go.microsoft.com/fwlink/?LinkId=56206](http://go.microsoft.com/fwlink/?LinkId=56206).  
  
    > [!NOTE]
    >  You should confirm that your NLB cluster is working properly outside of the BizTalk Server context before continuing.  
  
    > [!NOTE]
    >  To set up hardware-based NLB, refer to your hardware provider's documentation.  
  
### To update the BAM configuration to reflect the location of the cluster  
  
1. Use the BAM Management Utility to get the current BAM configuration. To do this, click **Start**, click **Run**, and type [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm get-config -FileName:MyConfig.xml.  
  
2. Replace the local host name with the name of the NLB cluster. To do this, click **Start**, click **Run**, and type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\MyConfig.xml.  
  
3. For hardware-based NLB only, verify the configuration file has the following:  
  
   ```  
   <GlobalProperty Name="BAMVRoot">  
   http://<NLB IP Address>:portname/BAM</GlobalProperty>  
   ```  
  
   > [!NOTE]
   >  Steps 4 and 5 are not necessary when updating the BAM configuration on hardware-based NLB.  
  
4. Modify the following line to point to the NLB cluster by replacing the computer name (machinename) with the cluster name:  
  
   ```  
   <GlobalProperty Name=" BAMVRoot">  http://machinename:portname/BAM  
   </GlobalProperty>   
   ```  
  
5. Save the new configuration. To do this, click **Start**, click **Run**, and type [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm update-config -FileName:MyConfig.xml.  
  
### To edit the BAM portal web.config file to change the BAMmanagementService and QueryService URLs to point to the NLB server name. Note: This procedure is not necessary for hardware-based NLB.  
  
1. Open the web.config file using Notepad by clicking **Start**, clicking **Run**, typing notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config, and then clicking **OK**.  
  
2. Modify the following computer name (machinename) and the port name in the following two lines to point to the name of name of the cluster:  
  
   ```  
   <add key="BamQueryWSUrl" value="http://machinename:portname /BAM/BAMQueryService/BamQueryService.asmx" />  
   <add key="BamManagementWSUrl" value=" http://machinename:portname/BAM/BAMManagementService/BamManagementService.asmx" />   
   ```  
  
3. Save the file. To do this, click **File**, and then click **Save** on the Notepad menu bar.  
  
### To configure each additional computer in the cluster  
  
1. Copy the web.config file to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal folder on each additional computer in the cluster.  
  
   > [!NOTE]
   >  In the following steps all references to the **Program Files** folder will be **Program Files (x86)** for 64 bit computers.  
   > 
   > [!IMPORTANT]
   >  In the following steps, when you are creating the virtual directories, check to make sure they have the exact settings as the three BAM virtual directories created by the BizTalk Server Configuration on first computer. Confirm your file paths, the ASP.NET version, your directory permissions, and application pool.  Use the same domain service account to run the BAMAppPool on the computer you are setting up as you used when setting up the first computer. Make sure the BAMAppPool is running on all of the computers. There are two web.config files you must copy.  
   > 
   >  In addition to the web.config file [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal, you must copy the web.config file in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService and [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMQueryService to the same folders on this computer.  
  
2. For hardware-based NLB only, modify the following computer name (machinename) and the port name in the following two lines to point to the name of name of the cluster:  
  
   ```  
   <add key="BamQueryWSUrl" value="http://machinename:portname /BAM/BAMQueryService/BamQueryService.asmx" />  
   <add key="BamManagementWSUrl" value=" http://machinename:portname/BAM/BAMManagementService/BamManagementService.asmx" />  
   ```  
  
3. Create an application pool called BAMAppPool.  
  
   > [!NOTE]
   >  The directory path for the virtual directories should be %InstallationFolder%/BamPortal, %InstallationFolder%/BamPortal/BAMManagementService, and %InstallationFolder%/BamPortal/BAMQueryService.  
  
4. Create a virtual directory under the Default Website called BAM.  
  
5. Change the application pool of BAM virtual directory to BAMAppPool.  
  
   > [!NOTE]
   >  The directory path for the virtual directories should be %InstallationFolder%/BamPortal, %InstallationFolder%/BamPortal/BAMManagementService and %InstallationFolder%/BamPortal/BAMQueryService.  
  
6. Create a virtual directory called BAMManagementService under BAM.  
  
7. Change the application pool of BAMManagementService to BAMAppPool.  
  
   > [!NOTE]
   >  The directory path for the virtual directories should be %InstallationFolder%/BamPortal, %InstallationFolder%/BamPortal/BAMManagementService, and %InstallationFolder%/BamPortal/BAMQueryService.  
  
8. Create a virtual directory called BAMQueryService under BAM.  
  
9. Change the application pool of BAMQueryService to BAMAppPool.  
  
10. Use the INETMGR, located on the virtual directory Properites ASP NET Tab, to change the version for BAM, BAMMANAGEMENTSERVICE, and BAMQUERYSERVICE to set the version of the Applications to .NET Framework 4.  
  
11. Run aspnet_setreg.exe -k:"SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices\identity" -u:BAMWebServiceAccount  -p:Password.  The account specified here is the BAM Management Web Service User account.  
  
    > [!CAUTION]
    >  BAM Portal *only* runs in 32-bit mode. If IIS is installed on a 64-bit machine, ASP.NET 2.0 must be enabled in 32-bit mode. To do this, open IIS Manager, open **Application Pool**, select the application pool (BAMAppPool), and then click **Advanced Settings**. In **Enable 32-bit applications**, select **True**.  
    >   
    >  [Planning for the BAM Portal](../core/planning-for-the-bam-portal.md) lists additional requirements.  
  
12. Set the read ACLs for the AppPool user on WebServices by running SubInACL, a command-line tool that enables administrators to obtain security information about files, registry keys, and services, and to transfer this information from user to user, from local or global group to group, and from domain to domain.  
  
13. Download SubInAcl from [http://go.microsoft.com/fwlink/?LinkId=61990](http://go.microsoft.com/fwlink/?LinkId=61990).  
  
14. Open a command prompt. To do this, click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
15. Type the following at the command prompt: subinacl.exe /subkeyreg "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices" "/grant=Network Service=R"  
  
    > [!NOTE]
    >  The purpose of this command is to grant the BAM Application Pool user read access to the SOFTWAREMicrosoftBizTalk Server3.0BAMWebServicesidentity registry key. The example uses Network Service since it is the default used by IIS for Application Pool. If you do not use the default IIS settings, you should substitute the application pool user that your deployment uses.  
  
16. Type the following at the command prompt: subinacl.exe /keyreg "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0" "/grant=\<BAM WebService Account\>”  
  
    > [!NOTE]
    >  The purpose of this command is to grant the BAM Management Web Service User account read access to the SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices\Identity registry key.  
  
17. Verify that the identity that the application pool that the BAMManagement Web service runs under has read access to the ASPNET_SETREG key.  
  
18. Use the Computer Management administrator tool to add the BAM Management Web service user and the BAM application pool user account to the IIS Worker Process Group (IIS_WPG) and SharePoint services group (STS_WPG).  
  
19. Set the permissions on the temporary ASP.NET folders for the applications pool and Web service users: c:\windows\system32\cacls "%windir%\Microsoft.NET\Framework\ v2.0.\<min version number\>\Temporary ASP.NET Files" /T /E /G \<BAM WebService Account\>:F  
  
    > [!NOTE]
    >  You grant access to both the BAM Management Web Service User account and the BAM App Pool User account.  
  
## See Also  
 [Managing the BAM Portal](../core/managing-the-bam-portal.md)