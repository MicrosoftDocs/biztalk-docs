---
title: "Critical Failure2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 390ea015-86eb-4803-9c14-a1e49ce79822
caps.latest.revision: 3
---
# Critical Failure
When an application makes a protocol error in sending data, the local node rejects the data using a [Status-Acknowledge(Nack-2)](../Topic/Status-Acknowledge\(Nack-2\)1.md) with a sense code indicating the reason for failure. This message has a critical failure flag that indicates whether the local node has marked the session as unrecoverable. The sense codes are listed in [FMI Status, Error, and Sense Codes](../core/fmi-status-error-and-sense-codes.md).  
  
 If the error is noncritical, the application can proceed as if the message that caused the error had not been sent. If the error is critical, the local node issues a [Close(PLU) Request](../Topic/Close\(PLU\)%20Request1.md) to the application (providing that the primary logical unit (PLU) connection is open), which means that the application cannot communicate on the PLU-SLU session until an **UNBIND–BIND** sequence is received from the host. The local node also sends a **TERM-SELF** request to the host to elicit an **UNBIND**. Therefore, the application does not need to issue a **LOGOFF** request on the system services control point (SSCP) session.  
  
## See Also  
 [Application CANCEL](../core/application-cancel.md)   
 [Direction after Receiving a Negative Response](../core/direction-after-receiving-a-negative-response.md)   
 [Direction after Sending a Negative Response](../core/direction-after-sending-a-negative-response.md)   
 [RQR and CLEAR](../core/rqr-and-clear.md)   
 [STSN](../core/stsn.md)   
 [Link Service Failure](../core/link-service-failure.md)   
 [Local Node Failure](../core/local-node-failure.md)   
 [Client Failure](../core/client-failure.md)