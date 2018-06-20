---
title: "How to Restore Your Databases | Microsoft Docs"
ms.custom: ""
ms.date: "2016-05-10"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "backing up, log shipping"
  - "restoring [BAM], Star Schema database, Star Schema database [BAM], restoring"
  - "restoring, 64-bit environments"
  - "Star Schema database [BAM], restoring"
  - "restoring [BAM], Analysis database"
  - "log shipping"
  - "databases, restoring"
  - "Archive database [BAM], restoring"
  - "backing up, restoring"
  - "Analysis database [BAM], restoring"
  - "restoring [BAM], Archive database"
  - "restoring [BAM], Star Schema database"
  - "databases, restoring [64-bit environment]"
  - "Primary Import database [BAM], restoring"
  - "64-bit environments, restoring databases"
  - "restoring, databases"
ms.assetid: 0176932a-6b3d-4502-975b-a76296189092
caps.latest.revision: 52
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Restore Your Databases
You must restore all databases to the same mark to ensure a consistent transactional state among the databases. See [Marked Transactions, Full Backups, and Log Backups](../core/marked-transactions-full-backups-and-log-backups.md).  
  
 If there is only one server in the destination system, make sure that all of the log backup sets (except for the most recent set) have been restored. See [Viewing the History of Restored Backups](../core/viewing-the-history-of-restored-backups.md). If all the log backup sets have not been restored, and the restore job is not currently running, run the restore job (manually if necessary). If there are outstanding backup sets that can be restored, the job processes them until they are all restored.  
  
 If there are multiple servers in the destination system, all servers must be restored to the same backup set. View the restore history on each server and make sure that the most recent log backup set restored is the same on all servers. If it is not, you must manually run the restore job on each server that needs the most recent log backup set restored.  
  
 After all of the servers are on the same backup set, the final set can be manually restored.  
  
 The adm_BackupHistory table is the central history point for the log shipping process for the source system. All backup work performed is recorded to this table. All servers in your destination system read from this table to receive the information needed to perform their restore work.  
  
> [!NOTE]
>  If you restore the BAM Primary Import database from a backup, then you should also restore the BAM Archive, BAM Star Schema, and BAM Analysis databases by using a backup older than the BAM Primary backup. See [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md).  
> 
> [!NOTE]
>  If you move the full or log backups for a source database from the location in which the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job put them, you should update the associated row for that database in the bts_LogShippingDatabases table on the destination system by setting the LogFileLocation or DBFileLocation to the new location where the destination system should read the full/log backup files. This table is populated when you run the bts_ConfigureBtsLogShipping stored procedure. By default, these columns are set to null, which indicates that the destination system should read the backup files from the location stored in the adm_BackupHistory table.  
> 
> [!IMPORTANT]
>  Always keep a copy of your backup files in a secure location. Even if you have log backups, you cannot restore your databases without the backup files.  
  
## Prerequisites  
 Log in to SQL Server using an account that is a member of the sysadmin SQL Server role.  
  
### To restore your databases  
  
1. On the destination system, open **SQL Server Management Studio**, and connect to your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
2. Expand **SQL Server Agent**, and expand **Jobs**. Do the following:  
  
   1. Right-click the **BTS Log Shipping - Get Backup History** job and select **Disable**. The status changes to Success.  
  
   2. Right-click the **BTS Log Shipping - Restore Databases** job and select **Disable**. The status changes to Success.  
  
   3. Right-click the **BTS Log Shipping - Restore To Mark** and select **Start Job at Step**. Select **Step ID 1** and select **Start**.  
  
       When the status changes to **Success**, the SQL Server Agent jobs and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are restored to the destination system.  
  
   > [!IMPORTANT]
   >  If the **Status** is Error, select the link in the Message field to determine the cause. These jobs should have a Success status before continuing.  
  
3. On the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] where you edited the SampleUpdateInfo.xml file, open a command prompt, and go to:  
  
    32-bit computer: `%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`  
  
    64-bit computer: `%SystemDrive%\Program Files (x86)\Microsoft BizTalk Server <version>\Bins32\Schema\Restore`  
  
4. At the command prompt, type:  
  
    `cscript UpdateDatabase.vbs SampleUpdateInfo.xml`  
  
    This script updates all tables that store information about the location of other databases.  
  
   > [!IMPORTANT]
   > - Run UpdateDatabase.vbs on **one** server in the BizTalk group.  
   >   -   On 64-bit computers, you must run UpdateDatabase.vbs from a 64-bit command prompt. Note that the default command prompt on 64-bit computers is a 64-bit command prompt and is located at %SystemDrive%\windows\System32\cmd.exe.  
   >   -   The BizTalk EDI engine does not require any of its own modifications to SampleUpdateInfo.xml when restoring databases.  It relies on connectivity to the BizTalkDTADb database to access the EDI tables.  
  
5. Copy the edited SampleUpdateInfo.xml file to the following folder on **every** computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in this BizTalk group:  
  
    32-bit computer: Copy to `%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`  
  
    64-bit computer: Copy to `%SystemDrive%\Program Files (x86)\Microsoft BizTalk Server <version>\Bins32\Schema\Restore`  
  
6. On **each** computer in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group, open a command prompt, and go to:  
  
    32-bit computer: `%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`  
  
    64-bit computer: `%SystemDrive%Program Files (x86)Microsoft BizTalk Server <version>Bins32SchemaRestore`  
  
7. At the command prompt, type:  
  
    `cscript UpdateRegistry.vbs SampleUpdateInfo.xml`  
  
    This script updates all registry entries that store information about the location of other databases.  
  
   > [!IMPORTANT]
   >  Run UpdateRegistry.vbs on **every** server in the BizTalk group.  
   >   
   >  On 64-bit computers, you must run UpdateRegistry.vbs from a 64-bit command prompt.  Note that the default command prompt on 64-bit computers is a 64-bit command prompt and is located at %SystemDrive%\windows\System32\cmd.exe.  
  
8. Restart all the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services. See [How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).  
  
9. After restoring your databases, restart the Windows Management Instrumentation service:  
  
    1.  Open **services.msc**.  
  
    2.  Right-click **Windows Management Instrumentation**, and then select **Restart**.  
  
10. Open **BizTalk Server Administration**. Do the following:  
  
    1. Right-click the **BizTalk Group** and select **Remove**.  
  
    2. Right-click **BizTalk Server Administration** and select **Connect to Existing Group**.  
  
    3. In **SQL Server name**, select the name of the SQL Server instance that hosts the BizTalk Management database. When you select the SQL Server instance, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] automatically detects the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases on that computer.  
  
    4. In **Database name**, select your BizTalk Management database (**BizTalkMgmtDb** by default), and then select **OK**.  
  
       The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console adds the BizTalk group to the Administration console.  
  
       Your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is now restored and should be running. Next, configure the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job to start writing backups to a new destination server. You should also reconfigure a new destination system.  
  
> [!IMPORTANT]
>  If you are using the Rules Engine, after restoring the databases, you must restart the Rule Engine Update Service on every server in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group. See [How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).  
> 
> [!NOTE]
>  If you are using BAM, this is the time to restore the BAM databases. See [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md).  
  
## Next Steps  
 [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md)  
  
## See Also  
 [How to Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md)   
 [How to Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md)