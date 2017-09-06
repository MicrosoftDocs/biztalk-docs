---
title: "Backing Up and Restoring the BizTalk Server Databases | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "backing up, BizTalk Server"
  - "backing up, transaction logs"
  - "maintaining, restoring"
  - "restoring, BizTalk Server"
  - "maintaining, backing up"
  - "transaction logs"
ms.assetid: 7c08ce19-614c-4728-8dde-c40d4052339e
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Backing Up and Restoring the BizTalk Server Databases
This section provides information about how to back up and restore the BizTalk Server databases. You should follow the procedures in this section to ensure your ability to restore a consistent BizTalk Server environment in the event of a hardware failure. BizTalk Server performs distributed transactions across databases, so it is critical that you back up and then restore all databases.  
  
 BizTalk Server requires a customized backup process that uses full database backups and log backups in conjunction with transactional log marking. For information about this process, see [Marked Transactions, Full Backups, and Log Backups](../core/marked-transactions-full-backups-and-log-backups.md).  
  
## In This Section  
  
-   [Checklist: Back Up and Restore BizTalk Server Databases](../core/checklist-back-up-and-restore-biztalk-server-databases.md)  
  
-   [Best Practices for Backing Up and Restoring Databases](../core/best-practices-for-backing-up-and-restoring-databases.md)  
  
-   [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md)  
  
-   [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md)  
  
-   [Resolving Data Loss](../core/resolving-data-loss.md)  
  
-   [Advanced Information About Backup and Restore](../core/advanced-information-about-backup-and-restore1.md)