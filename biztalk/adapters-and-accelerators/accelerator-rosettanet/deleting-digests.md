---
title: "Deleting Digests | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deleting, digests"
  - "messages, digests"
  - "digests"
  - "databases, deleting digests"
  - "maintaining databases, deleting digests"
ms.assetid: bcc7cb11-2f6a-4996-ad50-040d41993e09
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deleting Digests
Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] stores digests for outgoing messages, so it can validate them against signal content. However, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not delete the digests after validation. Periodically, you may want to delete these digests to maintain system performance.  
  
## When and How to Delete Digests  
 Digests are stored in the MessageDigestHelper table of the BTARNDATA database. Periodically, you may want to delete these digests from the table by using a stored procedure that deletes only those digests that are older than a certain period. The MessageDigestHelper table contains a `TimeCreated` property that you can use for this purpose.  
  
 Create a stored procedure with the following SQL statement (as modified for your purposes), and run the stored procedure to delete old digests. This sample statement deletes all digests more than seven days old:  
  
```  
delete from MessageDigestHelper where datediff(day, TimeCreated, getutcdate()) > 7  
```  
  
> [!NOTE]
>  The stored procedure must include a call to `getutcdate`, not `getdate`, because all [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] databases use UTC (Universal Time Coordinate) time.  
  
## See Also  
 [Maintaining BTARN Databases](../../adapters-and-accelerators/accelerator-rosettanet/maintaining-btarn-databases.md)