---
description: "Learn more about: Critical Failure"
title: "Critical Failure2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Critical Failure
When an application makes a protocol error in sending data, the local node rejects the data using a [Status-Acknowledge(Nack-2)](./status-acknowledge-nack-2-2.md) with a sense code indicating the reason for failure. This message has a critical failure flag that indicates whether the local node has marked the session as unrecoverable. The sense codes are listed in [FMI Status, Error, and Sense Codes](../core/fmi-status-error-and-sense-codes1.md).  
  
 If the error is noncritical, the application can proceed as if the message that caused the error had not been sent. If the error is critical, the local node issues a [Close(PLU) Request](./close-plu-request2.md) to the application (providing that the primary logical unit (PLU) connection is open), which means that the application cannot communicate on the PLU-SLU session until an **UNBIND–BIND** sequence is received from the host. The local node also sends a **TERM-SELF** request to the host to elicit an **UNBIND**. Therefore, the application does not need to issue a **LOGOFF** request on the system services control point (SSCP) session.  
  
## See Also  
 [Application CANCEL](../core/application-cancel2.md)   
 [Direction after Receiving a Negative Response](../core/direction-after-receiving-a-negative-response1.md)   
 [Direction after Sending a Negative Response](../core/direction-after-sending-a-negative-response2.md)   
 [RQR and CLEAR](../core/rqr-and-clear1.md)   
 [STSN](../core/stsn2.md)   
 [Link Service Failure](../core/link-service-failure1.md)   
 [Local Node Failure](../core/local-node-failure2.md)   
 [Client Failure](../core/client-failure1.md)
