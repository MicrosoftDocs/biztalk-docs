---
title: "Client Failure2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61a7d89b-1149-4288-bbc1-aa6a7950edf2
caps.latest.revision: 3
---
# Client Failure
If the client computer fails, the local node terminates the application's PLU-SLU session (if it is active) by sending **TERM-SELF**. The system services control point (SSCP) and primary logical unit (PLU) connections are both marked as closed and cannot be reused without being reopened. Internally, the local node treats such a failure in the same way as the receipt of a [Close(SSCP) Request](../HIS2010/close-sscp-request1.md) from the application.  
  
## See Also  
 [Application CANCEL](../HIS2010/application-cancel1.md)   
 [Direction after Receiving a Negative Response](../HIS2010/direction-after-receiving-a-negative-response2.md)   
 [Direction after Sending a Negative Response](../HIS2010/direction-after-sending-a-negative-response1.md)   
 [Critical Failure](../HIS2010/critical-failure1.md)   
 [RQR and CLEAR](../HIS2010/rqr-and-clear2.md)   
 [STSN](../HIS2010/stsn1.md)   
 [Link Service Failure](../HIS2010/link-service-failure2.md)   
 [Local Node Failure](../HIS2010/local-node-failure1.md)