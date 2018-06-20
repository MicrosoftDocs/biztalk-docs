---
title: "Installation and Configuration Troubleshooting | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installing, troubleshooting"
  - "configuring, troubleshooting"
  - "troubleshooting, configuring"
  - "troubleshooting, installing"
ms.assetid: 25a2f6c5-c049-4042-8e38-4f7a2556e066
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Installation and Configuration Troubleshooting
## Setup is unable to deploy the RuntimeSchemas assembly  
  
### Symptom  
 The A4SWIFT Setup program was unable to deploy RuntimeSchemas.dll. If the assembly is not deployed manually after setup, the A4SWIFT Configuration Wizard fails.  
  
### Possible Cause  
 One of the following conditions exists:  
  
- The Runtime Schemas assembly was already deployed when you tried to perform an initial installation of A4SWIFT.  
  
- [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] was not started on the computer on which you tried to install A4SWIFT.  
  
- The Runtime Schemas assembly was already deployed when you tried to upgrade A4SWIFT, and was referenced by another assembly. This prevented undeployment of the Runtime Schemas assembly by the A4SWIFT upgrade program.  
  
### Solution  
 Proceed as follows, depending upon the nature of the problem:  
  
- If the Runtime Schemas assembly was already deployed when you attempted to run an initial installation of A4SWIFT, open BizTalk Explorer in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)], right-click the assembly [!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.FinancialServices.SWIFT.RuntimeSchemas, and then click Undeploy. Use the BizTalk Deployment Wizard to deploy the latest version of RuntimeSchemas.dll from *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Assemblies.  
  
- If [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] was not started, start [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] in the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] Service Manager. Use the BizTalk Deployment Wizard to deploy the latest version of RuntimeSchemas.dll from *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Assemblies.  
  
- If the Runtime Schemas assembly was already deployed when you tried to upgrade A4SWIFT, and was referenced by another assembly, undeploy the referencing assembly in BizTalk Explorer, and undeploy RuntimeSchemas.dll in BizTalk Explorer. Use the BizTalk Deployment Wizard to deploy the latest version of RuntimeSchemas.dll from *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Assemblies.  
  
## After the Web Components feature is removed, Message Repair and Reconciliation is incorrectly shown as uninstalled  
  
### Symptom  
 After you remove the Web Components for Message Repair and New Submission feature of A4SWIFT, you cannot uninstall, install, or configure the Message Repair and Reconciliation feature (or A4SWIFT Components). If Message Repair and Reconciliation is installed, A4SWIFT does not recognize that the feature is installed. If you attempt to install, modify, or remove Message Repair and Reconciliation from within Add/Remove Programs (displayed from Control Panel), Add/Remove Programs will indicate that the feature is not installed.  
  
### Possible Cause  
 You were removed from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators group after you had installed the Web Components for Message Repair and New Submission feature and the Message Repair and Reconciliation feature. If you then remove the Web Components feature (which you can do without being a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators group), the A4SWIFT setup program will remove files that the Message Repair and Reconciliation feature has a dependency on. These files include ConfigFramework.exe.  
  
### Solution  
 If you encounter this problem, proceed as follows:  
  
1. In the Computer Management window, add yourself back into the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrator group, log off the computer, and then log back on.  
  
2. Re-install the Web Components for Message Repair and New Submission feature.  
  
   > [!NOTE]
   >  Step 2 adds ConfigFramework.exe back into the A4SWIFT installation.  
  
3. Re-install the MRSR feature.  
  
4. If you still do not want the Web Components for Message Repair and New Submission feature, remove it.  
  
## Repairing A4SWIFT to add the Service folder can result in improper access permissions for that folder  
  
### Symptom  
 If you delete the folder *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Service from a properly configured A4SWIFT installation, and then run the Repair feature of A4SWIFT setup to add the Server folder back in the A4SWIFT installation, the access permissions for the Service folder will not be correct. The correct permissions are Full Control for A4SWIFT Administrators and Read & Execute for A4SWIFT Users.  
  
 This also occurs if you run the Repair feature of A4SWIFT setup when the Service folder exists. The access permissions, as set by the A4SWIFT Configuration Wizard, will be overwritten with incorrect values.  
  
### Possible Cause  
 Installing the Web Components for Message Repair and New Submission feature adds the Service folder. If you delete the folder and then run the Repair option of A4SWIFT setup to add the Web Components for Message Repair and New Submission, A4SWIFT setup does not run the configuration wizard (ConfigFramework.exe) to set the permissions for the folder. Because the configuration wizard has already been run, it is very difficult to run the wizard again to reset the configuration. As a result, the Repair option will re-create all deleted files and folders, but it will not set access permissions correctly.  
  
 The repair process also overwrites permissions for the Service folder if the folder exists when repair is run. As with the case of deleting the Service folder before running repair, it will be very difficult to run the configuration program to set the permissions. In this instance, as well, the permissions will be incorrect and you will have to manually set them.  
  
### Solution  
 If you encounter this problem, manually set the following access permissions for the Service folder:  
  
|Group or User Name|Permission|  
|------------------------|----------------|  
|A4SWIFT Administrators|Full Control|  
|A4SWIFT Users|Read & Execute|  
  
 To set these permissions, proceed as follows:  
  
 In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Service.  
  
1.  Right-click the Service folder, click **Properties**, and then click the **Security** tab.  
  
2.  In the Group or user names pane of the Service Properties dialog box, click **Add**, enter ***\<server name\>*\A4SWIFT Administrators**, and then click **OK**.  
  
    > [!NOTE]
    >  If the A4SWIFT Administrators group is a domain group, enter ***\<domain name\>*\A4SWIFT Administrators**.  
  
3.  Repeat step 2 for ***\<server name\>*\A4SWIFT Users**, or **\<*domain name*\>\A4SWIFT Users** if the A4SWIFT Users group is a domain group.  
  
4.  In the Group or user names pane, select **A4SWIFT Administrators**. In the Permissions pane, select **Allow** for **Full Control**.  
  
5.  In the Group or user names pane, select **A4SWIFT Users**. In the Permissions pane, click **Allow** for **Read & Execute**, **List Folder Contents**, and **Read**.  
  
6.  Click **OK**.  
  
## Upgrade results in a side-by-side installation of two versions of A4SWIFT  
  
### Symptom  
 When you attempt to upgrade to [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], previous versions of A4SWIFT may not be fully removed. If you run Add/Remove Programs from the Control Panel, the list of Currently Installed Programs might show the current and the previous versions.  
  
### Possible Cause  
 Any of the following conditions can cause the above to occur:  
  
- The user attempting to upgrade is not a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
- The [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] service (MSSQLSERVER) is stopped.  
  
- You performed a silent upgrade using the **setup.exe /addlocal** command.  
  
### Solution  
 To prevent a side-by-side installation of [!INCLUDE[btaA4SWIFToldest](../../includes/btaa4swiftoldest-md.md)] and [!INCLUDE[btaA4SWIFT2.3abbrev](../../includes/btaa4swift2-3abbrev-md.md)] occurring during upgrade, ensure that you (the logged-on user) are a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators group, and that the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] service (MSSQLSERVER) is started.  
  
 If you end up with a side-by-side installation of [!INCLUDE[btaA4SWIFToldest](../../includes/btaa4swiftoldest-md.md)] or [!INCLUDE[btaA4SWIFT2.1abbrev](../../includes/btaa4swift2-1abbrev-md.md)] and [!INCLUDE[btaA4SWIFT2.3abbrev](../../includes/btaa4swift2-3abbrev-md.md)], proceed as follows:  
  
1. Back up the data in the SWIFT Messages folder.  
  
2. Log on to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] as a member of the BTS Administrators group, and ensure that the MSSQLSERVER service is running.  
  
3. Remove the previous version of A4SWIFT.  
  
4. Upgrade to the latest version of A4SWIFT again. This time the upgrade will work, and no side-by-side installation will be created.  
  
5. Using the BizTalk Deployment Utility, manually undeploy [!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll, and then redeploy it from the Assemblies folder of your A4SWIFT installation location. For more information about this tool, see [BRE Deployment Utility](../../adapters-and-accelerators/accelerator-swift/bre-deployment-utility.md).  
  
## The uninstall or upgrade process may not complete correctly if you do not restart when prompted  
  
### Symptom  
 Uninstall or upgrade processes do not complete correctly.  
  
### Possible Cause  
 If you have not undeployed a project that references an existing deployed assembly, you may receive a prompt indicating that you must restart your system for A4SWIFT configuration changes to take effect. If you do not click **Yes** to restart immediately, some assemblies that were assigned for removal in the global assembly cache may not be removed, causing additional uninstall or upgrade processes to not complete correctly.  
  
### Solution  
 Undeploy any project that references an existing deployed assembly, and then run the uninstall or upgrade process again.  
  
## If the IIS Admin Service is stopped during setup, you must reconfigure the WebService feature  
  
### Symptom  
 The [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration Wizard does not configure the WebService feature correctly. You receive the following error:  
  
 "Unable to create MRSR artifacts: Unable to connect to the remote server."  
  
### Possible Cause  
 The IIS Admin Service was stopped when you ran the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration Wizard.  
  
### Solution  
 To complete the configuration process successfully, proceed as follows:  
  
1. Close the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration console.  
  
2. Restart the IIS Admin Service.  
  
3. Execute *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Configuration.exe.  
  
4. In the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration console, select **Unconfigure Features** and then select **WebService**.  
  
5. Ensure that the status of the WebService feature in the Configuration console is shown as unconfigured.  
  
6. Select **Apply Configuration**.  
  
   > [!NOTE]
   >  The A4SWIFT Configuration Wizard will now configure the WebService feature correctly.  
  
## A4SWIFT configuration will fail if the BizTalkServerApplication host was not created in BizTalk Server configuration  
  
### Symptom  
 The [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration Wizard does not configure the WebService feature correctly. You receive the following error:  
  
 "Unable to create MRSR artifacts: Object reference not set to an instance of an object."  
  
### Possible Cause  
 An In-Process Host and a Host Instance were not created during BizTalk Server Runtime configuration.  
  
### Solution  
 To repair the A4SWIFT configuration, proceed as follows:  
  
- Create a host in BizTalk Server Administration. There is no need to have a running instance now.  
  
- Run the RepairBAS tool in the *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools folder of the A4SWIFT installation.  
  
  To do so, proceed as follows:  
  
1.  Start **BizTalk Server Administration** console.  
  
2.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, then expand **BizTalk Group**, and then expand **Platform Settings.**  
  
3.  Right-click **Hosts**, point to **New**, and then select **Host**.  
  
4.  In the Host Properties screen, in the General pane, enter the following:  
  
    -   Host name: **BizTalkServerApplication**  
  
    -   Type: **In-Process**  
  
    -   Windows group: **\<*domain*\>\BizTalk Application Users** (or the account that you set up during BizTalk Server configuration for running BizTalk In-Process applications)  
  
    -   In the Options section, select both **Allow Host Tracking** and **Make this the default host in the group**.  
  
5.  Click **OK**.  
  
6.  Click **Start** and then click Run. Type **cmd** and then click **OK**.  
  
7.  At the command prompt, navigate to *%programfiles%***\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools**.  
  
8.  Type **RepairBAS.exe** and then press **Enter**.  
  
## You must change the BRE Deployment configuration file when running the BRE Deployment Utility on a 64-bit computer  
  
### Symptom  
 The BRE Deployment Utility does not work correctly when you run it on a 64-bit computer or in a non-default directory (other than C:\Program Files\Microsoft BizTalk Accelerator for SWIFT) on a 32-bit computer.  
  
### Possible Cause  
 The BRE Deployment Utility will not work correctly until you change the paths in the BREDeployment.exe.config file located in the \<drive\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools folder.  
  
### Solution  
 Update the utility's configuration by opening BREDeployment.exe.config in Notepad, and changing the folders for the base policies, schemas, and vocabulary directories.  
  
## See Also  
 [Troubleshooting: Issues and Resolutions](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)