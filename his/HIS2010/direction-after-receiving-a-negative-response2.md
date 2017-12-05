---
title: "Direction after Receiving a Negative Response2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 07af68b2-0684-42e9-8c0b-e9cd77db33e3
caps.latest.revision: 3
---
# Direction after Receiving a Negative Response
Within the local node, error recovery for a half-duplex application (as specified by byte 7 bit 2 of the **BIND**) is assumed to be the responsibility of the host. However, the application must be aware that an error recovery state has been entered to obey the direction protocol.  
  
 When an application using half-duplex protocols (flip-flop or contention) receives a negative response to an inbound chain that it sent that does not refer to a race, it must assume receive state. The sense codes used for race conditions that do not require the transition to receive state are listed in the following table.  
  
|Sense code|Description|  
|----------------|-----------------|  
|0x080B|Bracket race error|  
|0x081B|Receiver in transmit mode|  
  
## See Also  
 [Application CANCEL](../HIS2010/application-cancel1.md)   
 [Direction after Sending a Negative Response](../HIS2010/direction-after-sending-a-negative-response1.md)   
 [Critical Failure](../HIS2010/critical-failure1.md)   
 [RQR and CLEAR](../HIS2010/rqr-and-clear2.md)   
 [STSN](../HIS2010/stsn1.md)   
 [Link Service Failure](../HIS2010/link-service-failure2.md)   
 [Local Node Failure](../HIS2010/local-node-failure1.md)   
 [Client Failure](../HIS2010/client-failure2.md)