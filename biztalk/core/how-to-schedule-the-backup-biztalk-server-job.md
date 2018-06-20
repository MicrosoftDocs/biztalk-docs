---
title: "Schedule the Backup BizTalk Server Job | Microsoft Docs"
description: Configure the Backup BizTalk Server job parameters, and set the schedule to run monthly, weekly, daily, or hourly
ms.custom: ""
ms.date: "11/02/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e89fff4-da87-4cdc-acc4-46f03c3269fc
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Schedule the Backup BizTalk Server Job
The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job runs as scheduled by the SQL Server Agent service. If you want to create more frequent or less frequent backups, you can change the schedule of the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job by using SQL Server Management Studio.  
  
## Prerequisites  
Sign in with an account that is a member of the SQL Server sysadmin fixed server role.  
  
## Schedule the Backup BizTalk Server job
  
1. On the SQL Server that hosts the BizTalk Management database, open **SQL Server Management Studio**.

2. In **Connect to Server**, enter the name of the SQL Server where the BizTalk Server databases reside, select the authentication type, and then **Connect**.  
  
3. In the Object Explorer, double-click **SQL Server Agent**, and then select **Jobs**.  
  
4. In the details pane, right-click **Backup BizTalk Server (BizTalkMgmtDb)**, and then select **Properties**.  
  
5. In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)**, under **Select a page**, select **Steps**.  
  
6. In the **Job step list**, select **BackupFull**, and then select **Edit**.  
  
7. In the **Job Step Properties - BackupFull**, in the **Command** box, update the command by changing the frequency to run a full backup: **'h'** (hourly), **'d'** (daily), **'w'** (weekly), **'m'** (monthly), **'y'** (yearly). Select **OK**.  
  
   > [!NOTE]
   >  The first time the Backup BizTalk Server job runs, it completes a full backup.  
    
8. Configure additional <strong>@frequency</strong> parameters:  
  
   - <strong>@ForceFullBackupAfterPartialSetFailure</strong>: The default value is **false**. When **false**, if the full backup fails, the system waits for the next cycle until the full backup is made.  
    
     > [!NOTE]
     >  If your <strong>@frequency</strong> setting is long (like weekly, monthly, yearly), then setting this parameter to **false** could be dangerous. In this scenario, it may be best to set this flag to **true**. When **true**, every time there is a failure, the system forces itself to create a full backup. There may be a small performance impact, but it’s safter to have a recoverable system.
  
   - <strong>@BackupHour</strong>: The default valueis NULL. This parameter is directly related to <strong>@Frequency</strong>. When you set the frequency to **h** (hourly), you set which hour of the day you want the full backup to run. You can choose a value between 0 (midnight) to 23 (11 PM). If left blank, the full backup runs every hour.  
    
      > [!NOTE]
       >  If you set this parameter with a number outside the 0 to 23 range (for example, 100 or -1), the system forces it to 0.
  
   - <strong>@UseLocalTime</strong>: An extra parameter that states to use local time. By default, the job works with UTC time. So if you live in Australia (which is UTC + 10 hours), your backup runs at 10am rather than midnight. As a best practice, it is recommended to set this to **1** (true).  
  
9. In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)**, under **Select a page**, click **Schedules**.  
  
10. In the **Schedule list**, click **MarkAndBackupLogSched**, and then click **Edit**.  
  
11. In the **Job Schedule Properties - MarkAndBackupLogSched**, in Schedule type, select **Recurring** from the drop-down list.  
  
     By default, the job is scheduled to run every 15 minutes.  
     
    > [!NOTE]
    >  You can change this value according to your requirements, but first test in non-production environment. Setting this value too low results in frequent backups, and adds to the background load in your SQL environment. Setting this value too high may increase the size of transaction logs, and impact performance. In some situations, it is recommended to leave the default value.    
  
12. Update the schedule if desired, and then select **OK**.  
  
    > [!NOTE]
    >  [Scheduling Jobs](https://docs.microsoft.com/sql/ssms/agent/schedule-a-job) provides more details.
  
13. In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)**, click **OK**.  
  
## More good stuff  
 [Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md)   
 [Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md)   
 [Restore Your Databases](../core/how-to-restore-your-databases.md)   
 [Advanced Information About Backup and Restore](../core/advanced-information-about-backup-and-restore1.md)
