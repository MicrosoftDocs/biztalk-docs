---
title: "How to Enable Automatic Archive Validation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "validating, archives [Tracking database]"
  - "archiving [Tracking database], validating archive"
ms.assetid: 406ca54a-6b1f-4bdb-9bad-bea5ea0f6e66
caps.latest.revision: 30
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Enable Automatic Archive Validation
Archive validation enables you to validate the archives as they are created. Before you can enable automatic archive validation, you must set up a secondary database server, also called a validation server. Because the archiving process is a simple backup, it is possible that the actual image stored on the disk can be corrupted due to a hardware issue.  
  
 Using the archive validation feature, you can ensure the archive (backup) was successful and can be restored. After an archive is created, the validation server is notified that a new archive has been created. The validation server attempts to restore the archive. A validation server must be another instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] different from the one in which the job is running. The version of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] on the validation server must be the same version as the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] used to host the databases.  
  
 If the restore is successful, the validation server communicates this information back to the BizTalk Tracking (BizTalkDTADb) database. Until a successful restore is completed, the purge job will not purge any more data.  
  
 If the restore is not successful, the validation server communicates this information back to the BizTalk Tracking database. The purge job creates another archive and awaits validation of the new archive. This prevents the possibility of a corrupted archive causing you to lose tracking data.  
  
## Prerequisites  
 You must be logged on with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.  
  
### To enable automatic archive validation  
  
1. On the validation server, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP2**, and then click **SQL Server Management Studio**.  
  
2. In the **Connect to Server** dialog box, specify the name of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] where you can validate the archive by performing a test of the restore process, and then click **Connect** to connect to the appropriate SQL Server.  
  
   > [!NOTE]
   >  This server should not be another [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database server as it reduces system performance when validating the archive.  
  
3. In **Microsoft SQL Server Management Studio**, click **File**, click **Open**, and then click **File**.  
  
4. In the **Open File** dialog box, browse to the following SQL script:  
  
   ```  
   %SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\BTS_Tracking_ValidateArchive.sql  
   ```  
  
   > [!NOTE]
   >  You might need to copy the script from the computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to the validation server.  
  
5. Click the **Query** menu, and then click **Execute**.  
  
   > [!NOTE]
   >  The BTS_Tracking_ValidateArchive.sql script only works if the folder where you are archiving your BizTalk Tracking (BizTalkDTADb) database is a network share.  
  
    The BTS_Tracking_ValidateArchive.sql script creates a SQL Server Agent job called ValidateArchive.  
  
6. The archiving and purging process potentially accesses and/or updates databases in different SQL Servers, so you must set up linked servers between the involved SQL Server instances. In **SQL Server Management Studio**, double-click **Server Objects**, right-click **Linked Servers**, and then click **New Linked Server**.  
  
    You must set up linked server between:  
  
   -   Each of your BizTalk MessageBox (BizTalkMsgBoxDb) databases and the BizTalk Tracking (BizTalkDTADb) database if they reside on different servers.  
  
   -   The BizTalk Tracking (BizTalkDTADb) database and the validating server for archive validation.  
  
   -   The service accounts for the SQL Server Agent on the computer hosting the BizTalk MessageBox (BizTalkMsgBoxDb) database must have the db_datareader and db_datawriter permissions for the BizTalk Tracking (BizTalkDTADb) database on the linked server.  
  
   > [!NOTE]
   >  The account used for running the job should have Database Operator (DBO) privileges on both the databases.  
  
7. In the **New Linked Server** dialog box, on the **General** page, in **Linked server**, enter the name of the server you want to link to.  
  
    For example, the server hosting the BizTalk MessageBox (BizTalkMsgBoxDb) database, BizTalk Tracking (BizTalkDTADb) database, or the validation server.  
  
8. Under **Server type**, click **SQL Server**, and then click **OK**.  
  
9. In **Microsoft SQL Server Management Studio**, double-click **SQL Server Agent**, and then click **Jobs**.  
  
10. In the **Object Explorer Details** pane, right-click **ValidateArchive**, and then click **Properties**.  
  
11. In the **Job Properties - ValidateArchive** dialog box, under **Select a page**, click **Steps**.  
  
12. In the **Job step list**, click **validate**, and then click **Edit**.  
  
13. On the **General** page, in the **Command** box, in the command, **exec dtasp_ValidateArchive null, null**, replace null, null with the name of the server hosting the BizTalk Tracking database, surrounded by single quotes, followed by the name of the BizTalk Tracking database, surrounded by quotes, and then click **OK**. For example:  
  
     **exec dtasp_ValidateArchive '** *\<TrackingServerName\>* **', '** *\<TrackingDatabaseName\>* **'**  
  
> [!NOTE]
>  The ValidateArchive job does not have a schedule and you should not configure a schedule for it. Instead, the DTA Purge and Archive (BizTalkDTADb) job starts this job automatically when an archive is created.  
  
## See Also  
 [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md)