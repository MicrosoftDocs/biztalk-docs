---
title: "Deleting Orphan Attachments | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "maintaining databases, deleting orphaned attachments"
  - "databases, deleting orphaned attachments"
  - "attachments"
ms.assetid: 38280464-9c9d-4890-9fc5-4b8031dd3f88
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deleting Orphan Attachments
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] stores attachments for received messages. In certain circumstances, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] saves the attachment, but deletes the associated message from the MessagesToLOB table, resulting in an orphan attachment. This can occur when you submit a message that has an attachment and has a manifest that is not valid, for example, a manifest in which NumberOfAttachments = 0. Periodically, you may want to delete orphan attachments to maintain system performance.  
  
## How to Delete Orphan Attachments  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] stores attachments in the Attachments table of the BTARNDATA database. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] stores the associated messages in the MessagesToLOB table. An orphan attachment results when the attachment has an `outMessageID` property that does not correspond to the `MessageID` property of a message in the MessagesToLOB table.  
  
 Periodically, you may want to delete attachments from the table by using a stored procedure that deletes only those attachments that do not have a corresponding message in the MessagesToLOB table. A sample SQL statement for the stored procedure is:  
  
```  
delete from attachments where outMessageID not in (select messageid from messagestolob)  
```  
  
 Additionally, it is recommended that you delete attachments that are older than a certain period, and do not require any more investigation. The Attachments table contains a `TimeCreated` property that you can use to delete old attachments. This process is similar to the process used to delete old digests. For a sample SQL statement for a stored procedure that deletes old digests, see [Deleting Digests](../../adapters-and-accelerators/accelerator-rosettanet/deleting-digests.md).  
  
 It is also recommended that you index the Attachments and MessagestoLOB tables on the respective MessageID columns.  
  
## See Also  
 [Maintaining BTARN Databases](../../adapters-and-accelerators/accelerator-rosettanet/maintaining-btarn-databases.md)