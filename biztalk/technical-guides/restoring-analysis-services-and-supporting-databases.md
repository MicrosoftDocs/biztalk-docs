---
title: "Restoring Analysis Services and Supporting Databases | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 490ad0fb-7805-4ebc-9bc5-117d52d7c3a8
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Restoring Analysis Services and Supporting Databases
There are two [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services databases that must be restored in a disaster recovery scenario:  
  
- BAM Analysis (BAMAnalysis)  
  
- Tracking Analysis Server (BizTalkAnalysisdb)  
  
  The BAM [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases may be backed up as part of the Backup BizTalk Server job if BAM is enabled but not configured.  
  
> [!NOTE]  
>  The BAM Primary Import database is always backed up as part of the Backup BizTalk Server job because it participates in DTC transactions.  
  
 The following BAM databases will be part of the Backup BizTalk Server job if BAM is enabled but not configured:  
  
- BAMStarSchema  
  
- BAMArchive  
  
  Follow the steps in [How to Restore Databases in the Backup BizTalk Server Job](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md) to restore these databases.  
  
  **Otherwise,**  
  **if BAM is enabled and is also configured with BM.exe, the correct set of BAM databases must be restored together as a set.** To ensure that a complete set of archived data is recovered, the BAM Archive database is backed up after the partition is copied into the BAM Archive, but before the partition is deleted from the BAM Primary Import database. This is performed by modifying the data maintenance SSIS package for each activity by inserting a step to back up the BAM Archive database before the last step "End Archiving."  
  
  The restore procedure for the BAM databases is: If the BAM Primary Import database is restored with the last backup date of x, restore the copies of the BAM Archive and BAM Star Schema databases that correspond to the latest date when the data maintenance SSIS package was run before the date of x.  
  
  After the correct set of BAM databases is identified, restore the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services databases using standard procedures as documented in the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online for restoring [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services databases.  
  
## See Also  
 [Backing Up the BAM Analysis and Tracking Analysis Server Databases](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)