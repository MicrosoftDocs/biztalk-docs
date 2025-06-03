---
description: "Learn more about: How to Back Up and Restore SQL Agent Jobs"
title: "How to Back Up and Restore SQL Agent Jobs"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Back Up and Restore SQL Agent Jobs
This topic describes how to back up and restore SQL Server Agent Jobs. You should back up your SQL jobs after you configure them.  
  
## BizTalk Server Jobs  
 The following SQL Server Agent jobs are associated with BizTalk Server. The jobs installed on each server are different depending on which features are installed and configured. Most of these jobs are created during BizTalk Server setup. Several are created when configuring log shipping.  
  
-   Backup BizTalk Server (BizTalkMgmtDb)  
  
-   CleanupBTFExpiredEntriesJob_BizTalkMgmtDb  
  
-   DTA Purge and Archive (BizTalkDTADb)  
  
-   MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb  
  
-   MessageBox_Message_Cleanup_BizTalkMsgBoxDb  
  
-   MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb  
  
-   MessageBox_Parts_Cleanup_BizTalkMsgBoxDb  
  
-   MessageBox_UpdateStats_BizTalkMsgBoxDb  
  
-   Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb  
  
-   PurgeSubscriptionsJob_BizTalkMsgBoxDb  
  
-   Rules_Database_Cleanup_BizTalkRuleEngineDb  
  
-   TrackedMessages_Copy_BizTalkMsgBoxDb  
  
-   BTS Log Shipping Get Backup History  
  
-   BTS Log Shipping Restore Database  
  
-   BTS Log Shipping Restore To Mark  
  
## Back up a job using a script  
  
1.  Open **SQL Server Management Studio**.  
  
2.  Expand **SQL Server Agent**, and expand **Jobs**.  
  
3.  Right-click the job you want to create a backup script for, and then select **Script Job as**.  
  
4.  Select **CREATE To** or **DROP To**, then select **New Query Editor Window**, **File**, or **Clipboard** to select a destination for the script. Typically, the destination is a file with a **.sql** extension.  
  
5.  Repeat this procedure from Step 3 for each job you want to script. Refer to the list of BizTalk Server related jobs to determine which jobs you need to script.  
  
     At a minimum, you should back up the **Backup BizTalk Server (BizTalkMgmtDb)** job after it is configured.  
  
## Restore a job from a script  
  
1.  Open **SQL Server Management Studio**.  
  
2.  On the **File** menu, **Open** the file containing the scripted job.  
  
3.  Execute the script to create the job.  
  
## Next Steps  
 [How to Back Up and Restore SQL Server Logins](../core/how-to-back-up-and-restore-sql-server-logins.md)
