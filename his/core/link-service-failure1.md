---
description: "Learn more about: Link Service Failure"
title: "Link Service Failure1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Link Service Failure
When the server running a link service fails, the local node is informed of this. It treats the problem as a link outage with outage code 0x0D. This is reported to any active 3270 emulation sessions as a communications check code (–+z_nnn). The local node will attempt periodically to reconnect to the link service.  
  
## See Also  
 [Application CANCEL](../core/application-cancel2.md)   
 [Direction after Receiving a Negative Response](../core/direction-after-receiving-a-negative-response1.md)   
 [Direction after Sending a Negative Response](../core/direction-after-sending-a-negative-response2.md)   
 [Critical Failure](../core/critical-failure2.md)   
 [RQR and CLEAR](../core/rqr-and-clear1.md)   
 [STSN](../core/stsn2.md)   
 [Local Node Failure](../core/local-node-failure2.md)   
 [Client Failure](../core/client-failure1.md)
