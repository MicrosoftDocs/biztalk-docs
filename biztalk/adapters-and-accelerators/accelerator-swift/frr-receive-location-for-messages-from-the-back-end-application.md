---
title: "FRR Receive Location for Messages from the Back-End Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FRR, receive locations"
  - "receive locations, FRR"
ms.assetid: da0ad616-800f-493f-822f-eca1224722ab
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# FRR Receive Location for Messages from the Back-End Application
To enable FIN response reconciliation (FRR), you must set up an FRR receive location that receives messages from the back-end application and routes them to the BizTalk MessageBox for consumption by the FRR orchestration. The receive location routes a message through a custom FRR receive pipeline that you must create with the following pipeline components:  
  
- The SWIFT disassembler in the Disassemble stage  
  
- The SWIFT FRR Decoder pipeline component in the Decoder stage  
  
- The SWIFT FRR CorrelationSet Resolver pipeline component in the Party Resolution stage  
  
  The receive port handles messages that have [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed==False and [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND==True. The transport mechanism is whatever the back-end application dictates.  
  
  This receive port uses the same custom receive pipeline that is used by the receive location for messages from SWIFT. However, the pipeline performs different functions for the two receive locations. In the receive location for messages from the back-end application, the SWIFT FRR CorrelationSet Resolver pipeline component initializes the correlation token.