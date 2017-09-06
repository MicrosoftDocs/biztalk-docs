---
title: "InterAct Adapter End-to-End Reliable Delivery | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac7c22f2-ee4a-4e9b-af40-da7eb58daf51
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# InterAct Adapter End-to-End Reliable Delivery
When sending messages or files to a recipient, we recommend that you ensure that the message or file is delivered, and that the business transaction(s) contained in these are executed no more times than anticipated.  
  
 When both entities communicating with each other can use a persistent storage (for example, provided by a persistent message-oriented middleware and an interface application using it), it is easy to implement a reliable delivery if the way to communicate the perceived status of the message is standardized.  
  
 The following figure shows an example of the structure of the E2EControl.  
  
 ![End&#45;to&#45;end control](../../adapters-and-accelerators/fileact-interact/media/63e39b43-118e-4572-9d75-21770253a1ee.gif "63e39b43-118e-4572-9d75-21770253a1ee")  
  
 The element in the example shown in the figure is sent within the SwInt:Request and delivered unchanged within the SwInt:RequestHandle to the receiving application. Line 02 allows assigning a unique identifier to the request. This unique identifier is repeated in each subsequent re-transmission of the same request.  
  
 The way this identifier is constructed is left to the implementer, but typically it is based on a system call such as uuidgen(), or it may be the result of computing a SHA-1 on the request to be sent (with a prefixed Sw:MsgId and then replace it by the base64 encoded SHA-1 string). The main requirement is that it is globally unique (with a very high probability).  
  
 The Sw:CreationTime is the time of creation of the original request. It is an optional parameter, but it is useful to limit eventual searches for previous communication attempts of this message.  
  
 The element Sw:PDIndication is present to indicate that this is a second or further attempt to transmit the message. The receiving application that is aware of the E2EControl can then use the Sw:MsgId to find back whether the message has been received or not. The optional Sw:EmissionList contains the time of the previous attempts. This time is the local time of the sender (in universal time) as got by the Sender when using the Sw:GetDateTime function. Again this could be useful to limit searches.  
  
## See Also  
 [InterAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [InterAct Adapter Components](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [InterAct Adapter Messages for Business Exchange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [InterAct Adapter Client Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [InterAct Adapter Server Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [InterAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [InterAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [InterAct Adapter Status Monitoring](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [InterAct Adapter Non-Repudiation](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)