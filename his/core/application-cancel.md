---
title: "Application CANCEL2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ef71ed9-dde0-422b-8060-9e7c29687452
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Application CANCEL
One of the parameters on the [Open(PLU) OK Response](../Topic/Open\(PLU\)%20OResponse1.md), which the application sends to the local node, specifies whether the application generates **CANCEL** (or **EC**) to terminate an inbound chain that has received a negative response. If this option is not selected, the local node generates a **CANCEL** request when it receives a negative response from the host to an incomplete chain.  
  
## See Also  
 [Direction after Receiving a Negative Response](../core/direction-after-receiving-a-negative-response.md)   
 [Direction after Sending a Negative Response](../core/direction-after-sending-a-negative-response.md)   
 [Critical Failure](../core/critical-failure.md)   
 [RQR and CLEAR](../core/rqr-and-clear.md)   
 [STSN](../core/stsn.md)   
 [Link Service Failure](../core/link-service-failure.md)   
 [Local Node Failure](../core/local-node-failure.md)   
 [Client Failure](../core/client-failure.md)