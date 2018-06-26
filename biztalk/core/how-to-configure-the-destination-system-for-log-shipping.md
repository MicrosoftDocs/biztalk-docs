---
title: "How to Configure the Destination System for Log Shipping | Microsoft Docs"
ms.custom: ""
ms.date: "2015-12-03"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "backing up, log shipping"
  - "system failures, preventing"
  - "log shipping"
  - "databases, backing up"
  - "backing up, databases"
  - "system failures, backing up"
  - "backing up, system failures"
ms.assetid: 7b4425f5-b105-4fb2-a503-94ca1e75ad55
caps.latest.revision: 54
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the Destination System for Log Shipping
Log shipping provides standby server capabilities to reduce downtime in the event of a system failure. Log shipping allows you to automatically send transaction logs from the source system to the destination system. At the destination system, the transaction logs are restored to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases; keeping them closely synchronized with the source databases.  
  
 Log shipping works in both single server and distributed server environments. The server or group of servers that contain live data is known as the source (or primary) system. The server or group of servers that are used to restore the database backups produced by the source (or primary) system is known as the destination (or secondary) system.  
  
 [About Log Shipping](https://docs.microsoft.com/sql/database-engine/log-shipping/about-log-shipping-sql-server) in the SQL documentation provides specific details.  
  
 You can use the following steps to create a destination system that consists of one server for a single source system. If the destination system contains multiple servers, repeat the steps on each destination server.  
  
> [!IMPORTANT]
>  Always keep a copy of your backup files in a secure location. Even if you have log backups, you cannot restore your databases without the backup files.  
  
## Prerequisites  
* Sign in as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
* Use the same version of SQL Server on the source and destination systems. SQL Server must be installed in the same relative location on the source and destination systems.  
  
* The directory for SQL transaction log (.LDF files) on the source system must also exist on the destination system. If this directory is not on the destination system, create the directory with the same name and permissions as on the source system.  
  
### Configure the destination system for log shipping  
  
1. On the destination system, open **SQL Server Management Studio**, and connect to your SQL Server. Select **master** from Available Databases.  
  
2. On the **File** menu, **Open** the following SQL script:  
  
   ```    
   %SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\LogShipping_Destination_Schema.sql  
   ```  
  
3. On the **Query** menu, select **Execute**.  
  
    The *LogShipping_Destination_Schema* drops and recreates the tables used for restoring the source databases on the destination system. This includes tables to store the list of databases being recovered, copies of the backup history imported from the source system's BizTalkMgmtDb database, and information about SQL Server Agent jobs configured to run against the source databases.  
  
4. On the **File** menu, **Open** the following SQL script:  
  
   ```    
   %SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\LogShipping_Destination_Logic.sql  
   ```  
  
5. On the **Query** menu, select **Execute**.  
  
6. On the computer or computers you have identified as the destination system, open **SQL Server Management Studio** and connect to the SQL Server.  
  
7. Select **New Query**. In the query window, paste the following command:  
  
   ```  
   exec bts_ConfigureBizTalkLogShipping @nvcDescription = '<MyLogShippingSolution>',  
   @nvcMgmtDatabaseName = '<BizTalkServerManagementDatabaseName>',  
   @nvcMgmtServerName = '<BizTalkServerManagementDatabaseServer>',  
   @SourceServerName = null, -- null indicates that this destination server restores all databases  
   @fLinkServers = 1 -- 1 automatically links the server to the management database  
   ```  
  
    Then:  
  
   1.  On the destination system, enable **[Ad Hoc Distributed Queries](https://docs.microsoft.com/sql/database-engine/configure-windows/server-configuration-options-sql-server)**.  
  
   2.  In the query window, replace *\<MyLogShippingSolution\>* with a meaningful description, surrounded by single quotes.  
  
   3.  In the query window, replace *\<BizTalkServerManagementDatabaseName\>* and *\<BizTalkServerManagementDatabaseServer\>* with the name and location of your source BizTalk Management database, surrounded by single quotes.  
  
   > [!NOTE]
   >  If you have more than one source server, you can restore each source server to its own destination server. On each destination server, in the **@SourceServerName = null** parameter, replace *null* with the name of the appropriate source server, surrounded by single quotes (for example, **@SourceServerName = 'MySourceServer',**).  
  
8. On the **Query** menu, select **Execute**.  
  
   > [!IMPORTANT]
   >  If the query fails, after you fix the problem with the query, you must start over from step 1 of this procedure to reconfigure the destination system.  
  
   > [!NOTE]
   >  The restore jobs on the destination system attempt to recreate the log and data files for each restored database in the same location as they existed on the source database server.  
  
9. On the destination system in **SQL Server Management Studio**, expand **SQL Server Agent**, and expand **Jobs**.  
  
     In the details pane, there are three new jobs:  
  
   - **BTS Log Shipping Get Backup History**  
  
      This BizTalk job moves backup history records from the source to the destination. It is scheduled by default to run every minute. This job runs as frequently as possible in order to move history records from the source to the destination. In the event of a system failure to the source system, the server that you identified as the destination system continues to process the history records that have already been imported.  
  
   - **BTS Server Log Shipping Restore Databases**  
  
      This BizTalk job restores backup files for the given databases for the source to the destination server. It is scheduled by default to run every minute. This job runs continuously without completing as long as there are backup files to restore. As an extra precaution, you can run this job an additional time to ensure that it is complete.  
  
   - **BTS Log Shipping Restore To Mark**  
  
      This BizTalk job restores all of the databases to a mark in the last log backup. This ensures that all of the databases are in a transactionally consistent state. In addition, this job re-creates all of the SQL Server Agent jobs on the destination system that had been on the source system.  
  
     > [!IMPORTANT]
     >  You should monitor these jobs to ensure that they do not fail.  
  
10. On the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], go to the following folder:  
  
     32-bit computer: %SystemDrive%\Program Files\Microsoft BizTalk Server \<version\>\Schema\Restore  
  
     64-bit computer: %SystemDrive%\Program Files (x86)\Microsoft BizTalk Server \<version\>\Bins32\Schema\Restore  
  
11. Right-click **SampleUpdateInfo.xml**, and select **Edit**. Do the following:  
  
    -   Replace all instances of **"SourceServer"** with the name of the source system.  
  
    -   Replace all instances of **"DestinationServer"** with the name of the destination system.  
  
    > [!IMPORTANT]
    >  Include the quotation marks around the name of the source and destination systems.  
    > 
    > [!NOTE]
    >  If you renamed any of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, you must also update the database names within the XML file.  
    > 
    > [!NOTE]
    >  If you have configured BAM, you must add the following lines in the **OtherDatabases** section of the **SampleUpdateInfo.xml** file for the BAMAlertsApplication and BAMAlertsNSMain databases:   
    > `<Database Name="BAM Alerts Application DB" oldDBName="BAMAlertsApplication" oldDBServer="SourceServer" newDBName=" BAMAlertsApplication" newDBServer="DestinationServer"/>`  
    > `<Database Name="BAM Alerts Instance DB" oldDBName="BAMAlertsNSMain" oldDBServer="SourceServer" newDBName="BAMAlertsNSMain" newDBServer="DestinationServer"/>`  
    > 
    >  If you changed the default name for these two databases, please use the actual database names.  
  
12. If you have more than one MessageBox database in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system, add another MessageBoxDB line to the list, and then set **IsMaster="0"** for the non-master databases.  
  
13. If you are using BAM or the Rules Engine, uncomment these lines as appropriate.  
  
14. If you have any custom databases, add them under the **\<OtherDatabases\>** section. See [How to Back Up Custom Databases](../core/how-to-back-up-custom-databases.md).  
  
15. When you are finished editing the file, save it, and exit.  
  
## Next Steps  
 [How to Restore Your Databases](../core/how-to-restore-your-databases.md)  
  
## See Also  
 [How to Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md)   
 [How to Schedule the Backup BizTalk Server Job](../core/how-to-schedule-the-backup-biztalk-server-job.md)   
 [How to Back Up Custom Databases](../core/how-to-back-up-custom-databases.md)