---
title: "How to Schedule the Backup BizTalk Server Job | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "backing up, scheduling"
  - "backing up, backup jobs"
  - "scheduling, backup jobs"
ms.assetid: 6e89fff4-da87-4cdc-acc4-46f03c3269fc
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Schedule the Backup BizTalk Server Job
The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job runs as scheduled by the SQL Server Agent service. If you want to create more frequent or less frequent backups, you can change the schedule of the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job by using SQL Server Management Studio.  
  
## Prerequisites  
 You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.  
  
### To schedule the Backup BizTalk Server job (SQL Server 2008)  
  
1.  On the SQL Server that hosts the BizTalk Management database, open **SQL Server Management Studio**.

2.  In the **Connect to Server** dialog box, specify the name of the SQL Server where the BizTalk Server databases reside and the appropriate authentication type, and then click **Connect**.  
  
3.  In the Object Explorer, double-click **SQL Server Agent**, and then click **Jobs**.  
  
4.  In the details pane, right-click **Backup BizTalk Server (BizTalkMgmtDb)**, and then click **Properties**.  
  
5.  In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)** dialog box, under **Select a page**, click **Steps**.  
  
6.  In the **Job step list**, click **BackupFull**, and then click **Edit**.  
  
7.  In the **Job Step Properties - BackupFull** dialog box, in the **Command** box, edit the command by changing the frequency to the desired interval at which to perform a full backup: **'h'** (hourly), **'d'** (daily), **'w'** (weekly), **'m'** (monthly), **'y'** (yearly), and then click **OK**.  
  
    > [!NOTE]
    >  The first time the Backup BizTalk Server job is run during a new period, a full backup is performed.  
    
8.  There is also couple of other parameters in the stored procedure that are related to the **@frequency** parameter:  
  
    1.  **@ForceFullBackupAfterPartialSetFailure**: The default value for this parameter is **false**, which mean if for some reason full backup fails, the system will wait for the next cycle until the full backup is made.  
    
    > [!NOTE]
    >  Having this this parameter as **false** could be dangerous if your **@frequency** is setting is high (something like weekly, monthly, yearly). In that scenarios it is recommended to set this flag to true, so every time there is a failure, the system will force itself to create a full backup. There will be little bit of performance impact, but it’s better to have a recoverable system.
  
    2.  **@BackupHour**: The default valueis NULL. This parameter is directly related to **@Frequency**. When you set the frequency to **h** (hourly), you basically can set which hour of the day you want the full backup to happen. You can choose a value between 0 (midnight) to 23 (11 PM). If left blank, the fullback will happen every hour.  
    
    > [!NOTE]
    >  If you try to set this parameter with a number outside that range: 0 to 23, for example: 100 or -1, the system will force it to 0.
  
    3.  **@UseLocalTime**: This is an extra parameter that you can also add that tells the procedure to use local time. By default, the job will work with UTC time, which means if you live in Australia (which is UTC + 10 hours), your backup will happen at 10am rather than midnight). So, as a best practice it is recommended to set this to **1** (true).  
  
9.  In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)** dialog box, under **Select a page**, click **Schedules**.  
  
10. In the **Schedule list**, click **MarkAndBackupLogSched**, and then click **Edit**.  
  
11. In the **Job Schedule Properties - MarkAndBackupLogSched** dialog box, in Schedule type, select **Recurring** from the drop-down list box (if it is not already selected).  
  
     By default, the job is scheduled to run every 15 minutes.  
     
    > [!NOTE]
    >  User can change this value according to their requirement, but it is recommended that you test in non-production environment before changing this value. Bringing this value too low will result in backup been taken frequently and putting lot of background load in your SQL environment. Setting this value too high may increase the size of transaction logs and impact performance. It is recommended to leave the default value.
    
  
12. Update the schedule as desired, and then click **OK**.  
  
    > [!NOTE]
    >  For more information about scheduling SQL Server Agent jobs, see "[Scheduling Jobs](http://go.microsoft.com/fwlink/?LinkId=195887)."  
  
13. In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)** dialog box, click **OK**.  
  
## See Also  
 [How to Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md)   
 [How to Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md)   
 [How to Restore Your Databases](../core/how-to-restore-your-databases.md)   
 [Advanced Information About Backup and Restore](../core/advanced-information-about-backup-and-restore1.md)
