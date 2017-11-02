---
title: "Client Failure1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5041852-076a-4829-84df-72730a3dd6c6
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Client Failure
If the client computer fails, the local node terminates the application's PLU-SLU session (if it is active) by sending **TERM-SELF**. The system services control point (SSCP) and primary logical unit (PLU) connections are both marked as closed and cannot be reused without being reopened. Internally, the local node treats such a failure in the same way as the receipt of a [Close(SSCP) Request](../Topic/Close\(SSCP\)%20Request1.md) from the application.  
  
## See Also  
 [Application CANCEL](../core/application-cancel.md)   
 [Direction after Receiving a Negative Response](../core/direction-after-receiving-a-negative-response.md)   
 [Direction after Sending a Negative Response](../core/direction-after-sending-a-negative-response.md)   
 [Critical Failure](../core/critical-failure.md)   
 [RQR and CLEAR](../core/rqr-and-clear.md)   
 [STSN](../core/stsn.md)   
 [Link Service Failure](../core/link-service-failure.md)   
 [Local Node Failure](../core/local-node-failure.md)