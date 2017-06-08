---
title: "Update References to the BAM Primary Import Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3da3b545-0d81-491b-bc37-0a980a7814b6
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Update References to the BAM Primary Import Database
If you backed up your BAM Primary Import database in the event of a system or data failure, you can restore that backup to a different computer and rename the backup.  
  
 The BAM Event Bus service moves event data from the MessageBox database to the BAM Primary Import database. The BAM Event Bus service includes fault tolerance logic that enables it to recover and restart from an unexpected failure without losing any data. For more information about the BAM Event Bus service, see the topic [Managing the BAM Event Bus Service](http://go.microsoft.com/fwlink/?LinkID=154194) (http://go.microsoft.com/fwlink/?LinkID=154194).  
  
 To restore the BAM Primary Import database, perform the steps in [How to Restore Databases in the Backup BizTalk Server Job](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md). In addition, you must update the BAM SSIS packages with the new server name and database name.  
  
## How to Update References to BAM Primary Import Database  
 For instructions on how to update references to BAM Primary Import database, [Updating References to the New BAM Primary Import Database](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_BAMPIRef).  
  
## See Also  
 [Backing Up the BAM Analysis and Tracking Analysis Server Databases](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)