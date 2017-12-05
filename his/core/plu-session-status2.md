---
title: "PLU Session Status2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e4cc754-f422-4e6d-ad18-87a3d17214a1
caps.latest.revision: 3
---
# PLU Session Status
While the primary logical unit (PLU) connection is open, the local node reports any changes of state to the application through [Status-Session](../core/status-session1.md) messages. There is only one **Status-Session** status code that can occur on the PLU connection, which is listed in the following table.  
  
|Status code|Description|  
|-----------------|-----------------|  
|BETB|The PLU session has made the transition from the in-bracket state to the between-bracket state. (For more information, see [Brackets](../core/brackets2.md).)|  
  
 [Status-Session Codes](../core/status-session-codes2.md) describes the **Status-Session** status codes.  
  
## See Also  
 [Opening the PLU Connection](../core/opening-the-plu-connection2.md)   
 [Outbound Chaining](../core/outbound-chaining1.md)   
 [Inbound Chaining](../core/inbound-chaining2.md)   
 [Segment Delivery](../core/segment-delivery2.md)   
 [Brackets](../core/brackets2.md)   
 [Direction](../core/direction2.md)   
 [Pacing and Chunking](../core/pacing-and-chunking2.md)   
 [Confirmation and Rejection of Data\]](../core/confirmation-and-rejection-of-data]2.md)   
 [Shutdown and Quiesce](../core/shutdown-and-quiesce2.md)   
 [Recovery](../core/recovery2.md)   
 [Application-Initiated Termination](../core/application-initiated-termination2.md)   
 [LUSTATs\]](../core/lustats]2.md)   
 [Response Time Monitor Data](../core/response-time-monitor-data2.md)