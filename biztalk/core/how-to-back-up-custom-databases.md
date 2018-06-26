---
title: "How to Back Up Custom Databases | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "custom databases"
  - "customizing, custom databases"
  - "backing up, custom databases"
ms.assetid: 86bebf3c-968e-4fad-9dab-ced1b04aaac7
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Back Up Custom Databases
Because your custom databases are not installed with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], they are not included in the default list of databases to be marked and backed up by the Backup BizTalk Server job. If you want the Backup BizTalk Server job to back up your custom databases, you must manually add the databases to the Backup BizTalk Server job.  
  
## Prerequisites  
  
1. SQL Server must be configured to use the full recovery model to ensure the integrity of data in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database backup sets.  For more information see [Log Shipping](../core/log-shipping.md).  
  
2. To back up your custom databases, you must be logged on with a user account that has access to each of the databases you are backing up.  
  
    BizTalk Server includes a SQL Server role named BTS_BACKUP_USERS so that the user account you use to back up your databases does not require System Administrator permissions within SQL Server, except for the primary server controlling the backup process.  
  
    When setting up the user account that you are using to back up your databases, note the following:  
  
   -   You must create a SQL Server logon account for this user, and assign this user to the BizTalk BTS_BACKUP_USERS role on each server.  
  
   -   The BizTalk Server backup jobs can be configured to run under a user account that is different than the one used for the SQL Server Agent service.  
  
   -   You must configure the SQL Server Agent service to run under a domain account. If all databases are on the same computer, you can configure SQL Server Agent to use a local account.  
  
### To back up custom databases  
  
1. Build the objects in the new database:  
  
   - Browse to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema directory, and then run Backup_Setup_All_Procs.sql and Backup_Setup_All_Tables.sql against all your custom databases that you want to back up. This creates the necessary procedures, table, and role and assigns permissions to the stored procedures.  
  
2. Perform the following configurations:  
  
   -   Link the SQL server that is hosting the BizTalk Management database to the SQL server hosting the new database. The account used to run the SQL Server Agent service on the management SQL Server must be a domain account that is mapped to each computer holding a database to be backed up. If the databases are on the same computer you can skip this step. This is done automatically.  
  
   -   Add a login on the SQL server hosting the new database for the account running the SQL Server Agent service on the Mgmt SQL Server. If the databases are on the same computer you can skip this step.  
  
   -   Add a user in the new database for the login created in the previous step and add them to the BTS_BACKUP_USERS role. This role is created and granted Execute permissions on the necessary procedures by the scripts in step 1.  
  
3. Using SQL Server Enterprise Manager or SQL Server Management Studio, in the BizTalk Management (BizTalkMgmtDb) database, modify the **adm_OtherBackupDatabases** table to include a row for each of your custom databases.  
  
4. Type the new server and database names in the corresponding columns, as shown in the following table.  
  
   |Column|Value|  
   |------------|-----------|  
   |DefaultDatabaseName|The friendly name of your custom database.|  
   |DatabaseName|The name of your custom database.|  
   |ServerName|The name of the computer running SQL Server.|  
   |BTSServerName|The name of the BizTalk Server. This value is not used, but it must contain a value nonetheless.|  
  
   The next time you run the Backup BizTalk Server job, it will back up your custom databases.  
  
## See Also  
 [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md)   
 [Advanced Information About Backup and Restore](../core/advanced-information-about-backup-and-restore1.md)