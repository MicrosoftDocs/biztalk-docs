---
title: "Link Service Failure1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dfd4de53-4ef3-401b-b14c-f5fee76a9781
caps.latest.revision: 3
---
# Link Service Failure
When the server running a link service fails, the local node is informed of this. It treats the problem as a link outage with outage code 0x0D. This is reported to any active 3270 emulation sessions as a communications check code (–+z_nnn). The local node will attempt periodically to reconnect to the link service.  
  
## See Also  
 [Application CANCEL](../core/application-cancel.md)   
 [Direction after Receiving a Negative Response](../core/direction-after-receiving-a-negative-response.md)   
 [Direction after Sending a Negative Response](../core/direction-after-sending-a-negative-response.md)   
 [Critical Failure](../core/critical-failure.md)   
 [RQR and CLEAR](../core/rqr-and-clear.md)   
 [STSN](../core/stsn.md)   
 [Local Node Failure](../core/local-node-failure.md)   
 [Client Failure](../core/client-failure.md)