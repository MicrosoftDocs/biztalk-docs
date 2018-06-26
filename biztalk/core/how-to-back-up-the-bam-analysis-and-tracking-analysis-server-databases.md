---
title: "How to Back Up the BAM Analysis and Tracking Analysis Server Databases | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "backing up, DTS packages"
  - "backing up [BAM], Tracking Analysis Server database"
  - "backing up [BAM], OLAP cubes"
  - "backing up [BAM], DTS packages"
  - "purging, OLAP cubes"
  - "Analysis database [BAM], backing up"
  - "scheduling, BAM backups"
  - "backing up [BAM], Analysis database"
  - "OLAP cubes, purging"
  - "backing up, BAM"
  - "backing up [BAM], database order"
  - "DTS packages, backing up"
  - "backing up [BAM], Star Schema database"
  - "backing up [BAM], scheduling"
  - "Tracking Analysis Server database [BAM], backing up"
  - "Star Schema database [BAM], backing up"
ms.assetid: d39e3491-ab54-44f2-990a-7b8ee86f0501
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Back Up the BAM Analysis and Tracking Analysis Server Databases
The Business Activity Monitoring (BAM) Analysis database and the Tracking Analysis Server database store content in SQL Server Analysis Services cubes. The Backup BizTalk Server job does not back up these databases. Instead, to backup these databases, you must use SQL Server Analysis Manager.  
  
 After you back up these databases, you may want to purge the OLAP cubes. When you purge the OLAP cubes, you must also perform the following steps:  
  
1. Before you purge the OLAP cubes, in the BAMStarSchema database, truncate the fact table(s) for the cube you want to purge. The table naming convention is "bam_*\<CubeName\>*_Facts".  
  
2. After you purge the OLAP cubes, you must fully process active, completed, and virtual cubes.  
  
   For instructions about backing up the analysis databases, see "Archiving an Analysis Services Database" in SQL Server Books Online.  
  
   **Scheduling backups for the BAM databases**  
  
   If you are using BAM, verify that neither the BAM cube process nor data maintenance Data Transformation Services (DTS) packages are running when the backup package is scheduled to run.  
  
   To ensure consistent schema across all BAM databases, back up the BAM databases and DTS packages each time you deploy or undeploy a BAM activity.  
  
   Back up the BAM Analysis database and BAMStarSchema database each time you deploy or undeploy a BAM view.  
  
   Back up the BAM databases in the following order:  
  
3. Run the Backup BizTalk Server job to back up the BAMPrimaryImport database and your other BizTalk Server databases.  
  
4. Run the BAM data maintenance DTS package for all activities.  
  
    Incorporate these steps into a DTS package, and schedule the package to run on a regular basis. To ensure data integrity, make sure no other BAM cubing or data maintenance DTS packages run when this backup package is scheduled to run.  
  
    To ensure that you can recover a complete set of archived data if the BAMArchive database fails, back up the BAMArchive database after you copy the partition into the BAMArchive database, but before you delete the partition from the BAMPrimaryImport database. To do this, modify the data maintenance DTS package for each activity to insert a step to back up the BAMArchive database before the last step in the DTS package, "End Archiving."  
  
5. Back up the BAMAnalysis database, and then the BAMStarSchema database.  
  
## See Also  
 [Backing Up and Restoring the BizTalk Server Databases](../core/backing-up-and-restoring-the-biztalk-server-databases.md)