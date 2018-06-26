---
title: "Configure the Backup BizTalk Server Job | Microsoft Docs"
description: 
ms.custom: ""
ms.date: "11/22/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 026622c9-fcb4-4db0-af48-1379feb30372
caps.latest.revision: 42
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the Backup BizTalk Server Job
After you install and configure BizTalk Server, configure the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job to back up your data. 

**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2**, you can backup your databases and log files to an Azure blob storage account. 


## Overview
The **Backup BizTalk Server (BizTalkMgmtDb)** job includes the following steps:

-   Step 1 – **Set Compression Option**: Enable or disable compression during backup

-   Step 2 – **BackupFull**: Runs full database backups of the BizTalk Server databases

-   Step 3 – **MarkAndBackUpLog**: Backs up the BizTalk Server database logs

-   Step 4 – **Clear Backup History**: Choose how long the backup history is kept

To configure this job, you'll need to:  
  
-   Identify the primary and destination SQL Servers and other backup options
  
-   Choose a Windows user account to back up your databases, and create a SQL Server login for this account
  
-   Map SQL Server logins to the BTS_BACKUP_USERS database role in the BizTalk Server databases
  
-   Ensure MSDTC service is active on all nodes. Otherwise, adding a linked server between the source node and the destination node fails.
  
## Before you begin  
  
- Certain configuration and backup operations require membership in the sysadmin SQL Server role. To back up your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, sign in the primary server with an account that is a member of the SQL Server sysadmin Server role. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration adds the BTS_BACKUP_USERS database role. The user account you use to back up your databases does not require System Administrator (sysadmin SQL Server role) permissions on all the SQL Servers that may be involved in a backup, except for the primary server.  
  
- Decide which sign in account you use to run your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database backups. You can use a local account, and you can use more than one account. But it is generally simpler and more secure to create one dedicated Windows domain user account specifically for this purpose. You must configure a SQL Server logon account for this user, and the user must be mapped to a SQL Server login for all of the SQL Servers that participate in the backup process, either as primary (source) or secondary (destination) servers. Assign this user to the BizTalk BTS_BACKUP_USERS database role for each of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases you back up.  
  
- The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job does not delete outdated backup files, so you need to manually manage those backup files to conserve disk space. After you have created a new full backup of your databases, you should move the outdated backup files onto an archival storage device to reclaim space on the primary disk. See the [SSIS packages](http://www.biztalkbill.com/2015/05/26/ssis-packages-to-help-management-biztalk-server-environments/) to manage these files.  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not write tracking data directly to the BizTalk Tracking database; rather it caches the data in the MessageBox database, and then moves it to the BizTalk Tracking database. If MessageBox data loss occurs, some tracking data may also be lost.  
  
## Prerequisites  
* Sign in to SQL Server using an account that is a member of the sysadmin SQL Server role.  
  
* Configure the SQL Server Agent service to run under a domain account (recommended, although local accounts can be used), with a mapped user login on each instance of SQL Server.  

* To use an Azure blob storage account, you need a [general purpose storage account](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account#create-a-storage-account), a container within your blob storage account, a [shared access signature](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url#SAS) (SAS), and a [SQL credential using the SAS](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url#credential). Once created, have your blob service endpoint URL ready, which is something like https://<em>yourstorageaccount</em>.blob.core.windows.net/*containername*. 

    > [!TIP]
    > If you don't have an existing blob storage account configured with a SAS, then the [SAS PowerShell script](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url#SAS) can create it, and the container. [SQL Server Backup to URL](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url) provides an overview, and the specific steps.
  
## Configure the job  
  
1. On the SQL Server that hosts the BizTalk Management database, open **SQL Server Management Studio**, and connect to your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
2. Expand **SQL Server Agent**, and expand **Jobs**.  
  
3. Right-click **Backup BizTalk Server (BizTalkMgmtDb)** and select **Properties**. In the job properties, select **Steps**.  
  
4. Select the **Set Compression Option** step, and select **Edit**:  

   This step calls the `sp_SetBackupCompression` stored procedure in the BizTalk management database (BizTalkMgmtDb) to set the value on the `adm_BackupSettings` table. The stored procedure has one parameter: <strong>@bCompression</strong>. By default, it is set to **0** (backup compression is off). To apply compression, change the value to **1**:  
  
   ```  
   exec [dbo].[sp_SetBackupCompression] @bCompression = 1 /*0 - Do not use Compression, 1 - Use Compression */  
   ```  
  
    Select **OK**.  
  
5. Select the **BackupFull** step, and select **Edit**. In the **Command** box, update the parameter values:  
  
   1. **Frequency**: The default is **d** (daily); which is the recommended setting. Other values include **h** (hourly), **w** (weekly), **m** (monthly), or **y** (yearly).  
  
   2. **Name**: The default is **BTS**. The name is used as part of the backup file name.  
  
   3. **Location of backup files**: Replace '*\<destination path\>*' with the full path (the path must include the single quotes) to the computer and folder where you want to back up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, or the blob service endpoint URL to an Azure blob storage account.  

      > [!IMPORTANT]
      > - If you enter a local path, then you have to manually copy all the files to the same folder on the destination system whenever the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job creates new files.  
      > 
      >      To use a remote path, enter a UNC share such as \\\\*\<ServerName\>*\\*\<SharedDrive\>*\\, where *\<ServerName\>* is the name of the server where you want the files, and *\<SharedDrive\>* is name of the shared drive or folder.  
      > 
      >      Backing up data over a network is subject to any network issues. When using a remote location, verify the backup succeeded when the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job finishes.  
      > - To avoid potential data loss, configure the backup disk to be a different disk than the database data and log disks. This is necessary so you can access the backups if the data or log disk fails.  
      > - When backing up to an Azure blob account, enter the **Blob service endpoint** URL and the container name, which are listed in your blob service properties in the [Azure portal](https://portal.azure.com).

   4. Optional. **Force full backup after partial backup failures** (@ForceFullBackupAfterPartialSetFailure): The default is **0**. If a log backup fails, no full backups are ran until the next full backup frequency interval is reached. Replace with **1** if you want a full backup ran whenever a log backup failure occurs.
    
   5. Optional. **Local time hour for the backup process to run** (@BackupHour): The default is **NULL**. The backup job is not associated with the time zone of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer, and runs at midnight UTC time (0000). If you want to backup at a specific hour in the time zone of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer, enter an integer value from 0 (midnight) to 23 (11 PM) as the local time hour. 

   6. Optional. **Use local time** (@UseLocalTime): Tells the procedure to use local time. The default value is **0**, and uses current UTC time – GETUTCDATE() – 2007-05-04 01:34:11.933. If set to **1**, then it uses local time – GETDATE() – 2007-05-03 18:34:11.933
  
   In the following example, daily backups are created at 2am, and stored in the m:\ drive:  
  
   ```  
   exec [dbo].[sp_BackupAllFull_Schedule]   
   'd' /* Frequency */,   
   'BTS' /* Name */,   
   'm:\BizTalkBackups' /* location of backup files */,   
   '0' /* 0 (default) or 1 ForceFullBackupAfterPartialSetFailure */,   
   '2' /* local time hour for the backup process to run */  
   ```  

   In the following example, weekly backups are created at midnight UTC time, and stored in your Azure blob account: 

   ```  
   exec [dbo].[sp_BackupAllFull_Schedule]   
   'w' /* Frequency */,   
   'BTS' /* Name */,   
   'http://yourstorageaccount.blob.core.windows.net/yourcontainer/' /* location of backup files */,   
   '1' /* 0 (default) or 1 ForceFullBackupAfterPartialSetFailure */
   ```  

    Select **OK**.  
  
6. Select the **MarkAndBackupLog** step, and select **Edit**. In the **Command** box, update the parameter values:  
  
   1. <strong>@MarkName</strong>: This is part of the naming convention for backup files: \<Server Name\>\_\<Database Name\>**\_Log\_**\< Log Mark Name \>\_\<Timestamp\>  
    
   2. <strong>@BackupPath</strong>: Full destination path (including single quotes) to the computer and folder to store the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database logs, or the Azure blob storage account and container. The *\<destination path\>* can also be local or a UNC path to another server.  
  
      The MarkAndBackupLog step marks the logs for backup, and then backs them up.  
  
   > [!IMPORTANT]
   >  To avoid **potential data loss** and for **performance improvement**, the *\<destination path\>* should be set to a different computer, or hard drive, different from what is used to store the original database logs.  
  
    Select **OK**.  
  
7. Select the **Clear Backup History** step, and select **Edit**. In the **Command** box, update the parameter values:  
  
   1. <strong>@DaysToKeep</strong>: Default value is **14 days**. Determines how long the backup history is kept in the `Adm_BackupHistory` table. Periodically clearing the backup history helps maintain the `Adm_BackupHistory` table to an appropriate size. 
    
   2. Optional. <strong>@UseLocalTime</strong>: Tells the procedure to use local time. The default value is 0. It uses current UTC time – GETUTCDATE() – 2007-05-04 01:34:11.933. If set to 1, then it uses local time – GETDATE() – 2007-05-03 18:34:11.933
  
   ```  
   exec [dbo].[sp_DeleteBackupHistory] @DaysToKeep=14, @UseLocalTime =1 
   ```  
  
   > [!NOTE]
   >  This step **does not** delete backup files from the destination path.  
    
    Select **OK** and close all property windows.  
  
8. Optional. Change the backup schedule. See [How to Schedule the Backup BizTalk Server Job](../core/how-to-schedule-the-backup-biztalk-server-job.md).  
  
   > [!NOTE]
   >  The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job runs the first time you configure it. By default, on subsequent runs, the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job completes a full backup once a day, and completes log backups every 15 minutes.  
  
9. Right-click the **Backup BizTalk Server** job, and select **Enable**. The status should change to **Success**.  

## Execute Backup_Setup_All_Procs.sql and LogShipping_Destination_Logic.sql

**[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2 (FP2)** used the Backup_Setup_All_Procs.sql and LogShipping_Destination_Logic.sql scripts in `\Program Files (x86)\Microsoft BizTalk Server *your version*\Schema`. 

If your Backup BizTalk Server job is already configured, and you want to switch to using Azure blob (instead of a disk), then also do the following: 

1. On the SQL Server, execute the `Backup_Setup_All_Procs.sql` script against all custom databases that are being backed up by the Backup BizTalk Server job. By default, FP2 automatically updates BizTalk databases; it does not update any custom databases (those databases in the `adm_OtherBackupDatabases` table in BizTalkMgmtDb).

    [Back Up Custom Databases](how-to-back-up-custom-databases.md) provides more details on custom databases. 

2. **If you use [log shipping](log-shipping.md)**, execute the LogShipping_Destination_Logic.sql script on the destination system within SQL Server. If you don't use log shipping, then do not execute this script.

    [Configure the Destination System for Log Shipping](how-to-configure-the-destination-system-for-log-shipping.md) provides more details on the destination system.

## sp_ForceFullBackup stored procedure  
  
The **sp_ForceFullBackup** stored procedure in the **BizTalkMgmtDb** database can be used to run an ad-hoc full backup of the data and log files. The stored procedure updates the adm_ForceFullBackup table with a value 1. The next time the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job is ran, a full database backup set is created.  
  
## Next Steps  
 [Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md)   
 [Schedule the Backup BizTalk Server Job](../core/how-to-schedule-the-backup-biztalk-server-job.md)  
 [Azure storage accounts](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account)  
 [SQL Server Backup to URL](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url)
