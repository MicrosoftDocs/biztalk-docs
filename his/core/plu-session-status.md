---
title: "PLU Session Status1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 829cebfb-deea-452a-af8f-ce9976e6f08c
caps.latest.revision: 3
---
# PLU Session Status
While the primary logical unit (PLU) connection is open, the local node reports any changes of state to the application through [Status-Session](../Topic/Status-Session1.md) messages. There is only one **Status-Session** status code that can occur on the PLU connection, which is listed in the following table.  
  
|Status code|Description|  
|-----------------|-----------------|  
|BETB|The PLU session has made the transition from the in-bracket state to the between-bracket state. (For more information, see [Brackets](../core/brackets.md).)|  
  
 [Status-Session Codes](../core/status-session-codes.md) describes the **Status-Session** status codes.  
  
## See Also  
 [Opening the PLU Connection](../core/opening-the-plu-connection.md)   
 [Outbound Chaining](../core/outbound-chaining.md)   
 [Inbound Chaining](../core/inbound-chaining.md)   
 [Segment Delivery](../core/segment-delivery.md)   
 [Brackets](../core/brackets.md)   
 [Direction](../core/direction.md)   
 [Pacing and Chunking](../core/pacing-and-chunking.md)   
 [Confirmation and Rejection of Data\]](../core/confirmation-and-rejection-of-data].md)   
 [Shutdown and Quiesce](../core/shutdown-and-quiesce.md)   
 [Recovery](../core/recovery.md)   
 [Application-Initiated Termination](../core/application-initiated-termination.md)   
 [LUSTATs\]](../core/lustats].md)   
 [Response Time Monitor Data](../core/response-time-monitor-data.md)