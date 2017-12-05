---
title: "Critical Failure1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf1d2b7e-54a6-41cd-a6d8-9e0c14eb07ab
caps.latest.revision: 3
---
# Critical Failure
When an application makes a protocol error in sending data, the local node rejects the data using a [Status-Acknowledge(Nack-2)](../core/status-acknowledge-nack-2-1.md) with a sense code indicating the reason for failure. This message has a critical failure flag that indicates whether the local node has marked the session as unrecoverable. The sense codes are listed in [FMI Status, Error, and Sense Codes](../core/fmi-status-error-and-sense-codes2.md).  
  
 If the error is noncritical, the application can proceed as if the message that caused the error had not been sent. If the error is critical, the local node issues a [Close(PLU) Request](../core/close-plu-request1.md) to the application (providing that the primary logical unit (PLU) connection is open), which means that the application cannot communicate on the PLU-SLU session until an **UNBIND–BIND** sequence is received from the host. The local node also sends a **TERM-SELF** request to the host to elicit an **UNBIND**. Therefore, the application does not need to issue a **LOGOFF** request on the system services control point (SSCP) session.  
  
## See Also  
 [Application CANCEL](../core/application-cancel1.md)   
 [Direction after Receiving a Negative Response](../core/direction-after-receiving-a-negative-response2.md)   
 [Direction after Sending a Negative Response](../core/direction-after-sending-a-negative-response1.md)   
 [RQR and CLEAR](../core/rqr-and-clear2.md)   
 [STSN](../core/stsn1.md)   
 [Link Service Failure](../core/link-service-failure2.md)   
 [Local Node Failure](../core/local-node-failure1.md)   
 [Client Failure](../core/client-failure2.md)