---
description: "Learn more about: Direction after Receiving a Negative Response"
title: "Direction after Receiving a Negative Response1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Direction after Receiving a Negative Response
Within the local node, error recovery for a half-duplex application (as specified by byte 7 bit 2 of the **BIND**) is assumed to be the responsibility of the host. However, the application must be aware that an error recovery state has been entered to obey the direction protocol.  
  
 When an application using half-duplex protocols (flip-flop or contention) receives a negative response to an inbound chain that it sent that does not refer to a race, it must assume receive state. The sense codes used for race conditions that do not require the transition to receive state are listed in the following table.  
  
|Sense code|Description|  
|----------------|-----------------|  
|0x080B|Bracket race error|  
|0x081B|Receiver in transmit mode|  
  
## See Also  
 [Application CANCEL](../core/application-cancel2.md)   
 [Direction after Sending a Negative Response](../core/direction-after-sending-a-negative-response2.md)   
 [Critical Failure](../core/critical-failure2.md)   
 [RQR and CLEAR](../core/rqr-and-clear1.md)   
 [STSN](../core/stsn2.md)   
 [Link Service Failure](../core/link-service-failure1.md)   
 [Local Node Failure](../core/local-node-failure2.md)   
 [Client Failure](../core/client-failure1.md)
