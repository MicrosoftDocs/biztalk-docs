---
title: "FRR Send Port for Messages to SWIFT | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FRR, send ports"
  - "send ports, FRR"
ms.assetid: 905c69a3-dff3-4a60-803d-dd617ffb6896
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# FRR Send Port for Messages to SWIFT
To enable FIN response reconciliation (FRR), you must set up an FRR send port that sends a message to SAA through the BizTalk Adapter for MQSeries. This send port routes a message through a custom FRR send pipeline component that you must create with the following pipeline components:  
  
- The SWIFT assembler in the Assemble stage  
  
- The SWIFTAsmFrrMQSeriesHelper pipeline component in the Encode stage  
  
  The SWIFTAsmFrrMQSeriesHelper pipeline component sets the MQMD_MsgID property of the outgoing message to the value of the FRRCorrelationToken property. It also assigns and promotes any other required context properties starting with "MQ" with values set at the pipeline design time. The send pipeline includes each property defined for MQSeries as a configurable property. Each value defaults to "Not Used".  
  
  The send port handles messages that have [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed==False and [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND==True. The transport mechanism is the BizTalk Adapter for MQSeries. For information about the transport properties, such as the fragmentation size, see the MQSeries documentation.