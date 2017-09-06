---
title: Uninstall BizTalk RosettaNet Accelerator (BTARN) on BizTalk Server | Microsoft Docs"
description: Undeploy artifacts, and unconfigure BTARN to remove the accelerator from BizTalk Server 
author: MandiOhlinger
manager: anneta

ms.date: "06/08/2017"
ms.prod: "biztalk-server"
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 
ms.author: mandia
---

# Uninstall the RosettaNet accelerator

## Before you begin
  
* If you only run **Setup.exe**, the uninstall process does not remove the Business Activity Monitoring (BAM) artifacts, the BizTalk artifacts, Internet Information Services (IIS) virtual directories, and application pools.  
  
* If you used the **Loopback** utility to create mirror agreements for a single-computer deployment, then run the tool with the **/disable <** **home organization** **>** option before deleting the partners in the **BTARN Administration Console**.  
  
* If this server is part of a multi-computer deployment, do not run the **BtarnClean** utility or manually undeploy the BTARN assemblies. Removing the artifacts on one computer breaks the functionality of the other computers.  If you want to uninstall BTARN from all the servers, then run the **BtarnClean** utility. 

  
## Undeploy the artifacts  

We recommend backing up your BAM artifacts before undeploying. 

1. Undeploy all the BAM artifacts that you deployed:  
  
    1.  At the command prompt, run the following command:  
  
         ```cd %ProgramFiles%\\<BizTalk Server installation directory\>\Tracking```
  
    2.  At the command prompt where the tracking UI was installed, run the following command:  
  
         ```bm remove-all DefinitionFile:"%ProgramFiles%\\<installation directory\>\BAMTracking\tracking.xml"```
  
        > [!NOTE]
        >  For more information about BAM, see [Managing Business Activity Monitoring](../../core/managing-bam.md) 
  
2.  Backup and delete all the agreements, partners, and home organizations from the BTARN Management Console. See the "Administering the BTARN Configuration" topic (in the Operations node of BTARN Help) for information about using the **BtarnConfig** utility to back up the agreements and partners.  
  
    > [!NOTE]
    >  * Stop and undeploy the BizTalk artifacts created by BTARN by using the [BtarnClean](btarnclean.md) utility.
	>  * Remove any additional artifacts that you deployed. See [Undeploying BizTalk Applications](../../core/undeploying-biztalk-applications.md) .
  
3.  From the BTARN Setup, locate the MSI\Program Files\Microsoft BizTalk Accelerator for RosettaNet\SDK folder. In the SDK folder, double-click **BTARNClean.exe**, and then select **Y** to continue, or **N** to cancel running the utility.  
  
    > [!NOTE]
    >  If your server is part of a multi-computer deployment scenario, you can skip step 3. Undeploying any shared resources breaks the functionality on the other servers in the deployment.  
  
4.  Undeploy any custom assemblies that you created and deployed.  
  
5.  At the command prompt, go to \Program Files\Microsoft BizTalk Server <your version>\Tracking. Run the following command: 

    ```BM UNDEPLOY ALL <drive\>:\Program Files\\<installation directory\>\BAMTracking\tracking.xml```
  
## Unconfigure BTARN
  
1.  Locate and run the following to unconfigure BTARN:  
  
     ***<drive\>***  **:\Program Files\\<installation directory\>\Configuration.exe /u**  
  
2.  In Control Panel, double-click **Add or Remove Programs**.  
  
3.  In the **Currently installed programs** list, click **Microsoft BizTalk Accelerator for RosettaNet**, and then click **Change/Remove**.  
  
4.  In the **Program Maintenance** dialog box, select **Remove**, and then click **Next**.  
  
5.  In the **Summary** dialog box, click **Uninstall**.  
  
6.  In the **Uninstall Completed** dialog box, click **Finish**.  
  
    > [!NOTE]
    >  The uninstallation process does not remove the BTARN databases (BTARNARCHIVE, BTARNCONFIG, and BTARNDATA). You must manually remove them.  
  
7.  Open **SQL Server Management Studio**.  
  
8.  In the **Connect to Server** dialog box, click **Connect**.  
  
9. Expand the **Databases** node in the left pane. Right-click one of the BTARN databases, and then click **Delete**.  
  
10. In the **Delete Object** dialog box, select **Close Existing Connections**, and then click **OK**.  
  
