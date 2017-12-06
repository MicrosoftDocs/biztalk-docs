---
title: "Direction after Receiving a Negative Response1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 709d58f7-c8b8-4000-bdb3-305714bbf4e3
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Direction after Receiving a Negative Response
Within the local node, error recovery for a half-duplex application (as specified by byte 7 bit 2 of the **BIND**) is assumed to be the responsibility of the host. However, the application must be aware that an error recovery state has been entered to obey the direction protocol.  
  
 When an application using half-duplex protocols (flip-flop or contention) receives a negative response to an inbound chain that it sent that does not refer to a race, it must assume receive state. The sense codes used for race conditions that do not require the transition to receive state are listed in the following table.  
  
|Sense code|Description|  
|----------------|-----------------|  
|0x080B|Bracket race error|  
|0x081B|Receiver in transmit mode|  
  
## See Also  
 [Application CANCEL](../core/application-cancel.md)   
 [Direction after Sending a Negative Response](../core/direction-after-sending-a-negative-response.md)   
 [Critical Failure](../core/critical-failure.md)   
 [RQR and CLEAR](../core/rqr-and-clear.md)   
 [STSN](../core/stsn.md)   
 [Link Service Failure](../core/link-service-failure.md)   
 [Local Node Failure](../core/local-node-failure.md)   
 [Client Failure](../core/client-failure.md)