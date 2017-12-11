---
title: "PLU Session Status1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 829cebfb-deea-452a-af8f-ce9976e6f08c
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# PLU Session Status
While the primary logical unit (PLU) connection is open, the local node reports any changes of state to the application through [Status-Session](../HIS2010/status-session1.md) messages. There is only one **Status-Session** status code that can occur on the PLU connection, which is listed in the following table.  
  
|Status code|Description|  
|-----------------|-----------------|  
|BETB|The PLU session has made the transition from the in-bracket state to the between-bracket state. (For more information, see [Brackets](../core/brackets1.md).)|  
  
 [Status-Session Codes](../core/status-session-codes1.md) describes the **Status-Session** status codes.  
  
## See Also  
 [Opening the PLU Connection](../core/opening-the-plu-connection1.md)   
 [Outbound Chaining](../core/outbound-chaining2.md)   
 [Inbound Chaining](../core/inbound-chaining1.md)   
 [Segment Delivery](../core/segment-delivery1.md)   
 [Brackets](../core/brackets1.md)   
 [Direction](../core/direction1.md)   
 [Pacing and Chunking](../core/pacing-and-chunking1.md)   
 [Confirmation and Rejection of Data\]](../core/confirmation-and-rejection-of-data]1.md)   
 [Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)   
 [Recovery](../core/recovery1.md)   
 [Application-Initiated Termination](../core/application-initiated-termination1.md)   
 [LUSTATs\]](../core/lustats]1.md)   
 [Response Time Monitor Data](../core/response-time-monitor-data1.md)