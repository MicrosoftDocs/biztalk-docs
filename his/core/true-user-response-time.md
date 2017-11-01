---
title: "True User Response Time2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6bfcd539-a7b0-40e8-bc07-219e9fead4e8
caps.latest.revision: 3
---
# True User Response Time
The true user response time is the time that the whole transaction takes to process. This is measured on the user-interface level. The difference in the true user response time and the external computer response time for Transaction Integrator (TI) transactions depends on how much of the processing is done on the client itself. For the FAT client approach, the opportunities to have "business logic" on the client side are greater than that of the thin client. The thin client processing typically involves just screen presentation processing delays.  
  
 The response time for FAT client transactions through TI, when the host processing time is virtually zero, is at maximum approximately 50 milliseconds for a small transaction (481 KB in/out). This is measured by the VCperform client application, and represents very closely the true end-user response time, missing only the screen presentation processing time. The amount of data conversion, heavy or light, and also using selection hints and UDTs did not affect the response time.  
  
 This response time includes the LAN delays for both TI processing and the backend host simulation processing; it is as close as possible to the optimum possible performance.  
  
## Response Time Contributors  
 On a properly tuned system, TI processing generally contributes less than 50 ms to the overall user response time. Two-phase commit (2PC) adds approximately 100 ms to this as a result of the disk I/O for the Microsoft Distributed Transaction Coordinator (DTC) logging.  
  
 The most significant contributor to the overall response time is naturally the host, where most of the work is done (business logic and database access). So the area to focus first in optimizing the performance is the host. To get a better idea of the response time and transaction volumes, use the TI performance counters.  
  
## See Also  
 [Major Elements Affecting Overall Performance](../core/major-elements-affecting-overall-performance.md)