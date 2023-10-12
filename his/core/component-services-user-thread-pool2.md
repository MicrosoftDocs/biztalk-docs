---
description: "Learn more about: Component Services User Thread Pool"
title: "Component Services User Thread Pool2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Component Services User Thread Pool
A thread from the Component Services user thread pool is allocated to a transaction as long as the host is processing the transaction (unit of work time). This occurs for both transactional (two-phase commit transactions), and nontransactional processing. If you have slow host or communication lines, or your transactions take a long time to process, you might have to adjust a registry entry to enable more threads for this pool. The default is 100 threads per COM+ application.  
  
## See Also  
 [Transaction Programs that Run for a Long Time](../core/transaction-programs-that-run-for-a-long-time2.md)   
 [Transaction Integrator Performance Guide](../core/transaction-integrator-performance-guide1.md)
