---
description: "Learn more about: Local Node Failure"
title: "Local Node Failure2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c7af4dd-eedb-4a5a-bbe8-58231c945db5
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Local Node Failure
If the local node fails, applications are informed of this by the path error return code from the Dynamic Access Module (DMOD) on the [sbpurcvx](./sbpurcvx1.md) call, or from the routing procedure. All connections that use the destination locality value for which the path error is reported are closed. The application must do the following:  
  
-   Clean up resources related to the closed connections, including resetting presentation spaces and displaying a communications check code  
  
     (–+z_nnn) on the status line.  
  
-   Attempt to reestablish connection with a local node by reinitiating the resource location process.  
  
## See Also  
 [Application CANCEL](../core/application-cancel2.md)   
 [Direction after Receiving a Negative Response](../core/direction-after-receiving-a-negative-response1.md)   
 [Direction after Sending a Negative Response](../core/direction-after-sending-a-negative-response2.md)   
 [Critical Failure](../core/critical-failure2.md)   
 [RQR and CLEAR](../core/rqr-and-clear1.md)   
 [STSN](../core/stsn2.md)   
 [Link Service Failure](../core/link-service-failure1.md)   
 [Client Failure](../core/client-failure1.md)
