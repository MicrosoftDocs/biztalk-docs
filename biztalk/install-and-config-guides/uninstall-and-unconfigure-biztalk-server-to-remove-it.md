---
title: "Uninstall and unconfigure BizTalk Server to remove it | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e9ea8757-ca49-421b-bf7b-89344201398a
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Uninstall and unconfigure BizTalk Server to remove it
Uninstall and unconfigure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. 
  
##  <a name="BKMK_BeforeYouBegin"></a> Before You Begin  
  
- Before you uninstall, you must un-configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
- This topic lists the different jobs, packages, and databases to be deleted. The names listed are the default names. Your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment may be using non-default names.  
  
- Complete the steps in the order listed. Otherwise, the uninstall is not complete.  
  
##  <a name="BKMK_Unconfigure"></a> Un-configure BizTalk Server  
  
1. Right-click **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration**, and select **Run as Administrator**.  
  
2. In the Configuration, select **Unconfigure Features**.  
  
3. Select the features you want to unconfigure, and select **OK**. If prompted to proceed, select **Yes**. To  remove everything from the computer, you can select all the features.  
  
4. Select **Next**, and continue through the wizard.  
  
   A log file is generated in a temp folder, similar to: C:\Users\username\AppData\Local\Temp\ConfigLog(8-29-2016 0h37m59s).log.  
  
##  <a name="BKMK_Uninstall"></a> Uninstall BizTalk Server Runtime Components  
  
1. Open **Programs and Features**.  
  
2. Select  your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] version from the list, and  **Uninstall**.  
  
3. **Remove** it, and continue through the wizard.  
  
   A log file is generated in a temp folder, similar to: C:\Users\\*username*\AppData\Local\Setup(083016 xxxxxx).htm  
  
##  <a name="BKMK_UninstallSSO"></a> Uninstall Enterprise Single Sign-On  
  
1. Open **Programs and Features**.  
  
2. Select **Microsoft Enterprise Single Sign-On** from the list, and **Uninstall**.  
  
3. **Remove** it, and continue through the wizard.  
  
   A log file is generated in a temp folder, similar to: C:\Users\\*username*\AppData\Local\Setup(083016 xxxxxx).htm  
  
##  <a name="BKMK_RemoveRemaining"></a> Delete SQL jobs, databases, and packages  
  
#### Delete SQL Server agent jobs  
  
1.  Open **SQL Server Management Studio** as Administrator.  
  
2.  In **SQL Server Management Studio**, connect to **Database Engine**, expand **SQL Server Agent**, and expand  **Jobs**.  
  
3.  Delete the following jobs (right-click the job, and select **Delete**):  
  
    -   Backup BizTalk Server (BizTalkMgmtDb)  
  
    -   CleanupBTFExpiredEntriesJob_BizTalkMgmtDb  
  
    -   DTA Purge and Archive (BizTalkDTADb)  
  
    -   MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb  
  
    -   MessageBox_Message_Cleanup_BizTalkMsgBoxDb  
  
    -   MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb  
  
    -   MessageBox_Parts_Cleanup_BizTalkMsgBoxDb  
  
    -   MessageBox_UpdateStats_BizTalkMsgBoxDb  
  
    -   Monitor BizTalk Server (BizTalkMgmtDb)  
  
    -   Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb  
  
    -   PurgeSubscriptionsJob_BizTalkMsgBoxDb  
  
    -   Rules_Database_Cleanup_BizTalkRuleEngineDb  
  
    -   TrackedMessages_Copy_BizTalkMsgBoxDb  
  
        > [!NOTE]
        >  If you deployed BAM, you may also need to remove the bam_\<*Cube Name*\>_\<*View Name*\> job.  
  
#### Delete BizTalk Server databases  
  
1.  In **Object Explorer**, expand **Databases**.  
  
2.  Delete the following databases (right-click the database, and select **Delete**):  
  
    -   BAMArchive  
  
    -   BAMPrimaryImport  
  
    -   BAMStarSchema  
  
    -   BizTalkDTADb  
  
    -   BizTalkMgmtDb  
  
    -   BizTalkMsgBoxDb  
  
    -   BizTalkRuleEngineDb  
  
    -   SSODB  
  
#### Remove SQL Server Integration Services packages  
  
1.  In **Object Explorer**,  **Connect** to **Integration Services**.  
  
2.  Expand **Stored Packages**, and expand **MSDB**.  
  
3.  Delete the packages with the following prefixes (right-click the package, and select **Delete**):  
  
    -   BAM_AN_\<*Cube Name*\>  
  
    -   BAM_DM_\<*View Name*\>  
  
