---
title: "How to Configure the Backup BizTalk Server Job | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tracking database, backing up"
  - "backing up, Tracking database"
  - "backing up, user accounts"
  - "backing up, MessageBox database"
  - "databases, backing up"
  - "MessageBox database, backing up"
  - "backing up, databases"
  - "backing up, prerequisites"
  - "configuring, backup jobs"
  - "backing up, warnings"
  - "backing up, backup jobs"
  - "user accounts, backing up"
  - "backing up, configuring"
ms.assetid: 026622c9-fcb4-4db0-af48-1379feb30372
caps.latest.revision: 42
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the Backup BizTalk Server Job
This topic lists the steps necessary to configure the Backup BizTalk Server job.  
  
 You must configure the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job before you can back up [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. To configure the backup, you need to perform most or all of the following tasks:  
  
-   Edit the SQL Server Agent **Backup BizTalk Server (BizTalkMgmtDb)** job to identify the primary and destination SQL Servers and other backup options.  
  
-   Choose a Windows user account to back up your databases and create a SQL Server login for this account.  
  
-   Map SQL Server logins to the BTS_BACKUP_USERS database role in the BizTalk Server databases.  
  
-   Ensure MSDTC service is active on all nodes. Else, adding a linked server between the source node and the destination node fails.  
  
## Before you begin  
  
-   Certain configuration and backup operations such as this one require membership in the sysadmin SQL Server role. To back up your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, you must be logged on at the primary server with an account that is a member of the SQL Server sysadmin Server role on the primary server. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration adds a database role named BTS_BACKUP_USERS so that the user account you use to back up your databases does not require System Administrator (sysadmin SQL Server role) permissions on all of the SQL Servers that may be involved in a backup, except for the primary server.  
  
-   You need to decide which login account you use to perform your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database backups. You can use a local account, and you can use more than one account, but it is generally simpler and more secure to create one dedicated Windows domain user account specifically for this purpose. You must configure a SQL Server logon account for this user, and the user must be mapped to a SQL Server login for all of the SQL Servers that participate in the backup process, either as primary (source) or secondary (destination) servers. Assign this user to the BizTalk BTS_BACKUP_USERS database role for each of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases you back up.  
  
-   The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job does not delete outdated backup files, so you need to manually manage those backup files to conserve disk space. After you have created a new full backup of your databases, you should move the outdated backup files onto an archival storage device to reclaim space on the primary disk. "BizTalk Bill" has downloadable [SSIS packages](http://www.biztalkbill.com/2015/05/26/ssis-packages-to-help-management-biztalk-server-environments/) to manage these files.  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not write tracking data directly to the BizTalk Tracking database; rather it caches the data in the MessageBox database and then moves it to the BizTalk Tracking database. If MessageBox data loss occurs, some tracking data may also be lost.  
  
## Prerequisites  
* Sign in to SQL Server using an account that is a member of the sysadmin SQL Server role.  
  
* Configure the SQL Server Agent service to run under a domain account (recommended, although local accounts can be used), with a mapped user login on each instance of SQL Server.  
  
## Configure the Backup BizTalk Server job  
  
1.  On the SQL Server that hosts the BizTalk Management database, open **SQL Server Management Studio**, and connect to your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
2.  Expand **SQL Server Agent**, and expand **Jobs**.  
  
3.  Right-click **Backup BizTalk Server (BizTalkMgmtDb)** and select **Properties**. In the job properties, select **Steps**.  
  
4.  Select the **Set Compression Option** step and select **Edit**. In the **Command** box, change the value to 1:  
  
    ```  
    exec [dbo].[sp_SetBackupCompression] @bCompression = 1 /*0 - Do not use Compression, 1 - Use Compression */  
    ```  
  
     Select **OK**.  
  
5.  Select the **BackupFull** step and select **Edit**. In the **Command** box, edit the parameter values:  
  
    1.  **Frequency**: The default is **d** (daily). This is the recommended setting. Other values include **h** (hourly), **w** (weekly), **m** (monthly), or **y** (yearly).  
  
    2.  **Name**: The default is **BTS**. The name is used as part of the backup file name.  
  
    3.  **Location of backup files**: Replace '*\<destination path>*' with the full path (the path must include the single quotes) to the computer and folder where you want to back up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.  
  
        > [!IMPORTANT]
        >  -   If you specify a local path, then you have to manually copy all the files to the same folder on the destination system whenever the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job creates new files.  
        >   
        >      To specify a remote path, enter a UNC share such as \\\\*\<ServerName>*\\*\<SharedDrive>*\\, where *\<ServerName>* is the name of the server where you want the files, and *\<SharedDrive>* is name of the shared drive or folder.  
        >   
        >      Backing up data over a network is subject to any network issues. When using a remote location, verify the backup succeeded when the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job finishes.  
        > -   To avoid potential data loss, configure the backup disk to be a different disk than the database data and log disks. This is necessary so you can access the backups if the data or log disk fails.  
  
    4.  **Force full backup after partial backup failures**: The default is **0** when not specified, which means that if a log backup fails, no full backups are done until the next full backup frequency interval is reached. Replace with **1** if you want a full backup to be made whenever a log backup failure occurs.  
  
    5.  **Local time hour for the backup process to run**: The default is NULL when not specified, which means that backup job is not associated with the time zone of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer and therefore runs at midnight UTC time (0000). If you want to backup to run at a particular hour in the time zone of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer, enter an integer value from 0 (midnight) to 23 (11 PM) as the local time hour for the **BackupHour** parameter.  
  
     In the following example, daily backups are created at 2am and stored in the m:\ drive:  
  
    ```  
    exec [dbo].[sp_BackupAllFull_Schedule]   
    'd' /* Frequency */,   
    'BTS' /* Name */,   
    'm:\BizTalkBackups' /* location of backup files */,   
    0 /* 0 (default) or 1 ForceFullBackupAfterPartialSetFailure */,   
    '2' /* local time hour for the backup process to run */  
    ```  
  
     Select **OK**.  
  
6.  Select the **MarkAndBackupLog** step and select **Edit**. In the **Command** box, replace **'***\<destination path>***'** with the full path (including single quotes) to the computer and folder where you want to store the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database logs. The *\<destination path>* may be local or a UNC path to another server.  
  
     The MarkAndBackupLog step marks the logs for backup, and then backs them up.  
  
    > [!IMPORTANT]
    >  To avoid potential data loss, the *\<destination path>* should specify a computer to store the database logs that is different from the computer with the original database logs.  
  
     Select **OK**.  
  
7.  Select the **Clear Backup History** step and select **Edit**. In the **Command** box, change **DaysToKeep=***\<number>* to the number of days you want to keep the backup history:  
  
    ```  
    exec [dbo].[sp_DeleteBackupHistory] @DaysToKeep=14  
    ```  
  
    > [!NOTE]
    >  The **DaysToKeep** parameter specifies how long the backup history is kept in the Adm_BackupHistory table. Periodically clearing the backup history helps to maintain the Adm_BackupHistory table at an appropriate size. The default value for the **DaysToKeep** parameter is 14 days.  
  
     Select **OK** and close all property windows.  
  
8.  Optional. Change the backup schedule. See [How to Schedule the Backup BizTalk Server Job](../core/how-to-schedule-the-backup-biztalk-server-job.md).  
  
    > [!NOTE]
    >  The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job runs the first time you configure it. By default, on subsequent runs, the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job performs a full backup once a day and performs log backups every 15 minutes.  
  
9. Right-click the **Backup BizTalk Server** job and select **Enable**. The status should change to **Success**.  
  
## sp_ForceFullBackup stored procedure  
  
> [!NOTE]
>  The sp_ForceFullBackup stored procedure in the BizTalkMgmtDb database can be used to help perform an ad-hoc full backup of the data and log files. The stored procedure updates the adm_ForceFullBackup table with a value 1. The next time the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job is ran, a full database backup set is created.  
  
## Next Steps  
 [How to Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md)  
  
## See Also  
 [How to Schedule the Backup BizTalk Server Job](../core/how-to-schedule-the-backup-biztalk-server-job.md)