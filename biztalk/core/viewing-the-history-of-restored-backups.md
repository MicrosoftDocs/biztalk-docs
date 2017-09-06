---
title: "Viewing the History of Restored Backups | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "restoring, history"
  - "backing up, history"
ms.assetid: 8852befa-b8e7-469d-b014-75c881907442
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Viewing the History of Restored Backups
To determine the last successful backup set restored, review the contents of the Master.dbo.bts_LogShippingHistory table. This table is populated by the Get Backup History job and updated by the Restore Databases job. When a backup is successfully restored, the Restored column is set to 1 and the RestoredDateTime is set to the current date and time.  
  
 When all of the databases being restored to the server from a particular backup set have been successfully restored, that backup set ID is written to the Master.dbo.bts_LogShippingLastRestoreSet table.  
  
## Gaps in the restore process  
 When reviewing records in the Master.dbo.bts_LogShippingHistory table, you may find gaps in the sets restored. This can occur for several reasons. However, you can still recover the stability of your destination system (which are your backup computers), even when gaps have occurred. A gap must be followed by a restore of a full backup set to repair the destination system. If a gap is not followed by a full backup set restore, the destination environment is not stable.  
  
> [!NOTE]
>  Full backups are only restored to initially create the database and to repair problems in the log history backup chain. In most cases full backup sets are not restored, as they are not part of the log backup chain.  
  
## See Also  
 [Advanced Information About Backup and Restore](../core/advanced-information-about-backup-and-restore1.md)