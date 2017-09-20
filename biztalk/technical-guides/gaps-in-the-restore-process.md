---
title: "Gaps in the Restore Process | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 616c4f36-8ed6-4b99-b97a-5635627dfc17
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Gaps in the Restore Process
When reviewing records in the Master.dbo.bts_LogShippingHistory table, you may observe gaps in restored sets. This can occur for several reasons. However, the stability of the destination system can be restored even when gaps have occurred. A gap must be followed by a restore of a full backup set to repair the destination environment. If a gap is not followed by a full backup set restore, the destination environment is not stable and cannot be restored in a consistent state.  
  
> [!NOTE]  
>  Full backups are only restored to initially create the database and to repair problems in the log history backup chain. As long as a problem does not occur with a restore, full backup sets are not restored, because they do not participate in the log backup chain.  
  
## See Also  
 [Troubleshooting Log Shipping](../technical-guides/troubleshooting-log-shipping.md)