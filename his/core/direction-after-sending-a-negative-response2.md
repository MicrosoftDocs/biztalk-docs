---
title: "Direction after Sending a Negative Response2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 02a78093-3219-40b2-8874-6315fc18fd60
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Direction after Sending a Negative Response
When an application using half-duplex flip-flop protocol sends a negative response to an outbound chain (or sends a [Status-Acknowledge(Ack)](./status-acknowledge-ack-2.md) to a **DATAFMI** message with **SDI** set) that does not refer to a race, the application must assume an error recovery pending state. The sense codes used for race conditions that do not require the transition to error recovery pending state are listed in the following table.  
  
|Sense code|Description|  
|----------------|-----------------|  
|0x080B|Bracket race error|  
|0x0813|Bracket bid reject (no RTR forthcoming)|  
|0x0814|Bracket bid reject (RTR forthcoming)|  
|0x081B|Receiver in transmit mode|  
  
 The application must therefore examine the sense code on an **SDI** message to detect such races.  
  
 Error recovery pending state differs from receive state only in one respect: The application can convey sense information to the host using **Status-Control(LUSTAT).** (For more information, see [LUSTATs](../core/lustats]1.md).) The **LUSTAT** must not have the change direction (CD) or end bracket (EB) flags set. (The host already has direction, and the bracket must not be terminated prematurely by the application.) Host Integration Server also enables the function management interface (FMI) application to send **Status-Control(LUSTAT)** in receive state.  
  
 An application using the half-duplex contention protocol does not have an error recovery pending state, and must enter contention state whenever it sends a negative response.  
  
> [!NOTE]
>  If the chain is canceled by the host with CD on the **CANCEL** , the application must assume send state.  
  
## See Also  
 [Application CANCEL](../core/application-cancel2.md)   
 [Direction after Receiving a Negative Response](../core/direction-after-receiving-a-negative-response1.md)   
 [Critical Failure](../core/critical-failure2.md)   
 [RQR and CLEAR](../core/rqr-and-clear1.md)   
 [STSN](../core/stsn2.md)   
 [Link Service Failure](../core/link-service-failure1.md)   
 [Local Node Failure](../core/local-node-failure2.md)   
 [Client Failure](../core/client-failure1.md)