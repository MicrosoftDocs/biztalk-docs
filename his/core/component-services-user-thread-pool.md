---
title: "Component Services User Thread Pool2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87cf2693-6eda-476b-a568-63fc15cd3243
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Component Services User Thread Pool
A thread from the Component Services user thread pool is allocated to a transaction as long as the host is processing the transaction (unit of work time). This occurs for both transactional (two-phase commit transactions), and nontransactional processing. If you have slow host or communication lines, or your transactions take a long time to process, you might have to adjust a registry entry to enable more threads for this pool. The default is 100 threads per COM+ application.  
  
## See Also  
 [Transaction Programs that Run for a Long Time](../core/transaction-programs-that-run-for-a-long-time.md)   
 [Transaction Integrator Performance Guide](../core/transaction-integrator-performance-guide.md)