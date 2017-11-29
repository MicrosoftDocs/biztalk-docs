---
title: "Scalability and Long-Running TPs1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ecf7ac29-3e49-41a5-8007-419a65ebeaa0
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Scalability and Long-Running TPs
When the transaction processing times (unit of work and commit times) become longer because of the nature of the transactions or an excessive load on the host, the behavior of the middle-tier software might change the throughput and end-user response time. This occurs because the number of active concurrent transactions increases and the middle-tier server is doing some level of transaction caching. For example, in a system that processes 200 TPS (transactions per second) at an average transaction response time of one second, the concurrent active transaction count at any give time is around 200. If the response time grows to five seconds, the concurrently active transactions grow to approximately 1000.  
  
## See Also  
 [Transaction Programs that Run for a Long Time](../core/transaction-programs-that-run-for-a-long-time.md)   
 [Transaction Integrator Performance Guide](../core/transaction-integrator-performance-guide.md)