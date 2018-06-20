---
title: "SWIFT Trailers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SWIFT Trailer schema"
  - "schemas, SWIFT"
  - "trailers [SWIFT]"
  - "SWIFT, trailers"
ms.assetid: b6d64584-0514-4c87-98c0-33755efc4695
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SWIFT Trailers
Each SWIFT message has one or more trailers as required by the message exchange and security requirements. System trailers, if applicable, follow user trailers. Each trailer within the Trailer Block appears within a subblock delimited by further pairs of curly brackets. Each subblock begins with three letters denoting the trailer type, followed by a colon.  
  
 The SWIFT Trailer schema (SWIFT Trailer.xsd) contains the format for the following:  
  
- The ending delimiter of the text block  
  
- User trailers (user and system information)  
  
- System trailers  
  
  The ending delimiter of the Text Block is "-}". The trailer block begins with "{5:". The contents of the trailer block include both user information (checksum, message authentication, proprietary authentication, and so on), and system information (delayed message, message reference, possible duplicate message, and so on). Trailers added by SWIFT also provide a third block, delimited by "{S:". The *SWIFT User Handbook*, "FIN Service Description" topic, describes in detail the contents of block 5. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] does not validate the contents of block S.  
  
  The actual FIN interface or the SWIFT network appends the trailers. If a message contains a trailer when [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receives the message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] carries the trailer with the message. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] does not raise an error if a message does not contain a trailer when [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receives the message. As with headers, all of the trailer entries, including the blocks themselves, are optional in [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].  
  
  This section contains:  
  
- [User Trailers](../../adapters-and-accelerators/accelerator-swift/user-trailers.md)  
  
- [System Trailers](../../adapters-and-accelerators/accelerator-swift/system-trailers.md)  
  
## See Also  
 [Working with Schemas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)