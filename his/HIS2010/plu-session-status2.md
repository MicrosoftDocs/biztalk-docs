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
While the primary logical unit (PLU) connection is open, the local node reports any changes of state to the application through [Status-Session](../HIS2010/status-session1.md) messages. There is only one **Status-Session** status code that can occur on the PLU connection, which is listed in the following table.  
  
|Status code|Description|  
|-----------------|-----------------|  
|BETB|The PLU session has made the transition from the in-bracket state to the between-bracket state. (For more information, see [Brackets](../HIS2010/brackets2.md).)|  
  
 [Status-Session Codes](../HIS2010/status-session-codes2.md) describes the **Status-Session** status codes.  
  
## See Also  
 [Opening the PLU Connection](../HIS2010/opening-the-plu-connection2.md)   
 [Outbound Chaining](../HIS2010/outbound-chaining1.md)   
 [Inbound Chaining](../HIS2010/inbound-chaining2.md)   
 [Segment Delivery](../HIS2010/segment-delivery2.md)   
 [Brackets](../HIS2010/brackets2.md)   
 [Direction](../HIS2010/direction2.md)   
 [Pacing and Chunking](../HIS2010/pacing-and-chunking2.md)   
 [Confirmation and Rejection of Data\]](../HIS2010/confirmation-and-rejection-of-data]2.md)   
 [Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)   
 [Recovery](../HIS2010/recovery2.md)   
 [Application-Initiated Termination](../HIS2010/application-initiated-termination2.md)   
 [LUSTATs\]](../HIS2010/lustats]2.md)   
 [Response Time Monitor Data](../HIS2010/response-time-monitor-data2.md)