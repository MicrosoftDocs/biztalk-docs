---
title: "Component Services User Thread Pool1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5de405b-48bd-40aa-be5b-9d7fc5101642
caps.latest.revision: 3
---
# Component Services User Thread Pool
A thread from the Component Services user thread pool is allocated to a transaction as long as the host is processing the transaction (unit of work time). This occurs for both transactional (two-phase commit transactions), and nontransactional processing. If you have slow host or communication lines, or your transactions take a long time to process, you might have to adjust a registry entry to enable more threads for this pool. The default is 100 threads per COM+ application.  
  
## See Also  
 [Transaction Programs that Run for a Long Time](../HIS2010/transaction-programs-that-run-for-a-long-time1.md)   
 [Transaction Integrator Performance Guide](../HIS2010/transaction-integrator-performance-guide2.md)