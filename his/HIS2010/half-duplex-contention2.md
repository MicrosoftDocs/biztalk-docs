---
title: "Half-Duplex Contention2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f731b7c-25f8-470c-81e8-55928888603c
caps.latest.revision: 3
---
# Half-Duplex Contention
For half-duplex contention, the initial direction state is contention. Half-duplex protocol operates during a chain (only one partner can send), but the direction state normally returns to contention at the end of each chain. The change direction indicator (CDI) in the response header (RH) is thus not required. However, if the CDI is used, direction is reserved for the receiving half-session. Therefore, if the application receives change direction (CD), it should assume send state and not expect to receive data. Conversely, if the application sends CD, it cannot send again until it has received a chain from the host.  
  
 In the event of an error being discovered by either half-session, the application must assume receive state, because the host is responsible for recovery.  
  
 If both half-sessions attempt to start a chain when the direction state is contention, the race is resolved in favor of the secondary application using a sense code of 0x081B. However, the possible window between the local node and the application means that the local node cannot determine when outbound Request Exception (RQE) data is received by the application. Therefore, if the local node receives data from the application while it determines that the half-duplex contention state is receive, it will reject it with a noncritical NACK-2 (0x2004 direction).  
  
 The following two figures illustrate the direction protocol for applications using half-duplex contention mode. The three figures in the previous topic would also be valid although CD does not need to be specified.  
  
 In the following figure, the application issues and receives data using half-duplex contention protocol without error.  
  
 ![](../core/media/his-32703n.gif "his_32703n")  
Application issues and receives data using half-duplex contention protocol without error  
  
 In the following figure, the half-duplex contention race is resolved in favor of the application.  
  
 ![](../core/media/his-32703na.gif "his_32703na")  
Resolving half-duplex contention race in favor of the application  
  
## See Also  
 [Opening the PLU Connection](../HIS2010/opening-the-plu-connection2.md)   
 [PLU Session](../HIS2010/plu-session1.md)   
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