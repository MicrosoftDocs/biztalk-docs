---
title: "Link Service Failure2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e393184-3363-4d2f-847f-20fc359326c8
caps.latest.revision: 3
---
# Link Service Failure
When the server running a link service fails, the local node is informed of this. It treats the problem as a link outage with outage code 0x0D. This is reported to any active 3270 emulation sessions as a communications check code (–+z_nnn). The local node will attempt periodically to reconnect to the link service.  
  
## See Also  
 [Application CANCEL](../core/application-cancel1.md)   
 [Direction after Receiving a Negative Response](../core/direction-after-receiving-a-negative-response2.md)   
 [Direction after Sending a Negative Response](../core/direction-after-sending-a-negative-response1.md)   
 [Critical Failure](../core/critical-failure1.md)   
 [RQR and CLEAR](../core/rqr-and-clear2.md)   
 [STSN](../core/stsn1.md)   
 [Local Node Failure](../core/local-node-failure1.md)   
 [Client Failure](../core/client-failure2.md)