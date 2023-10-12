---
description: "Learn more about: Partial Backup Sets"
title: "Partial Backup Sets"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Partial Backup Sets
When backing up the databases on the source system, problems may occur that result in a partial backup set. When this occurs, the Master.dbo.bts_LogShippingHistory table will contain a 0 in the **SetComplete** column for all records in the set.  
  
 These sets cannot be restored. As a result the log backup set chain is broken. The set must be ignored, as well as all log backup sets after it, up to the next full backup set. The restore job will automatically look for the next valid full backup set. If it does not find one, it fails and restores that set in order to repair the destination environment.  
  
 In most cases the source system will detect that a partial backup set has occurred and will automatically produce a full backup set the next time it runs if it is configured to do so.  
  
> [!NOTE]  
>  The most common cause of this problem is insufficient disk space for the file groups on the destination system.  
  
## See Also  
 [Troubleshooting Log Shipping](../technical-guides/troubleshooting-log-shipping.md)
