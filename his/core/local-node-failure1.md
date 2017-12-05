---
title: "Local Node Failure1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe1da900-8bcc-487e-92e2-80300eb60e2b
caps.latest.revision: 3
---
# Local Node Failure
If the local node fails, applications are informed of this by the path error return code from the Dynamic Access Module (DMOD) on the [sbpurcvx](../core/sbpurcvx2.md) call, or from the routing procedure. All connections that use the destination locality value for which the path error is reported are closed. The application must do the following:  
  
-   Clean up resources related to the closed connections, including resetting presentation spaces and displaying a communications check code  
  
     (–+z_nnn) on the status line.  
  
-   Attempt to reestablish connection with a local node by reinitiating the resource location process.  
  
## See Also  
 [Application CANCEL](../core/application-cancel1.md)   
 [Direction after Receiving a Negative Response](../core/direction-after-receiving-a-negative-response2.md)   
 [Direction after Sending a Negative Response](../core/direction-after-sending-a-negative-response1.md)   
 [Critical Failure](../core/critical-failure1.md)   
 [RQR and CLEAR](../core/rqr-and-clear2.md)   
 [STSN](../core/stsn1.md)   
 [Link Service Failure](../core/link-service-failure2.md)   
 [Client Failure](../core/client-failure2.md)