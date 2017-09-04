---
title: "Update References to the BAM Analysis Server and Star Schema Database Names | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 319caa26-1292-4453-a316-efca4fbffdb6
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Update References to the BAM Analysis Server and Star Schema Database Names
If you backed up your BAM Analysis database, in the event of a system or data failure you can restore that backup to a different computer and you can rename the backup.  
  
 To restore the BAM Analysis and Star Schema databases, perform the steps in [How to Restore Databases in the Backup BizTalk Server Job](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md). In addition, you must update the BAM [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Integration Services (SSIS) packages with the new server name and database name.  
  
## How to Update References to BAM Analysis Server and Star Schema Database Names  
 For instructions on how to update references to BAM Analysis server databases, see [Updating References to the New BAM Analysis Database](../technical-guides/how-to-move-the-bam-analysis-database1.md#BKMK_AnalyUpdate). For instructions on how to update references to the BAM Star Schema databases, see [Updating References to the New BAM Star Schema Database](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdate).