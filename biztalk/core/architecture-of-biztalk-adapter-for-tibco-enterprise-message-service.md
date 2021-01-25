---
description: "Learn more about: Architecture of BizTalk Adapter for TIBCO Enterprise Message Service"
title: "Architecture of BizTalk Adapter for TIBCO Enterprise Message Service | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "transmit adapter"
  - "one-way receive operations"
  - "architecture"
  - "one-way send operations"
  - "receive adapter"
ms.assetid: 304c7236-aacd-4761-8c33-e876b53e84ff
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Architecture of BizTalk Adapter for TIBCO Enterprise Message Service
Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) provides a means to exchange real-time business data between TIBCO EMS systems and BizTalk Server. The adapter enables interaction between an XML application and TIBCO EMS.  
  
 The adapter accepts XML messages that enable BizTalk applications to communicate with TIBCO EMS using one of the following:  
  
-   **Transmit Adapter**: Uses a static one-way send port to send a message to TIBCO EMS.  
  
-   **Receive Adapter**: Uses a static one-way receive port to receive messages from TIBCO EMS.  
  
## One-Way Send Operation  
 The following figure shows the architecture of a one-way send operation using BizTalk Adapter for TIBCO EMS.  
  
 ![](../core/media/tibcoems-architecture-send.gif "TIBCOEMS_architecture_send")  
  
## One-Way Receive Operation  
 The following figure shows the architecture for a one-way receive operation using BizTalk Adapter for TIBCO EMS.  
  
 ![](../core/media/tibcoems-architecture-receive.gif "TIBCOEMS_architecture_receive")  
  
## See Also  
 [Adapter Features](../core/adapter-features.md)   
 [Planning and Architecture](../core/planning-and-architecture16.md)
