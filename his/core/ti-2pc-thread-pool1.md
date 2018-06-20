---
title: "TI 2PC Thread Pool1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4080d93-8803-46e1-8ba9-ff39025f35bc
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TI 2PC Thread Pool
The Transaction Integrator (TI) two-phase commit (2PC) thread pool is different from the COM+ user thread pool. The TI 2PC thread pool is used only for 2PC transactions. The threads are precreated, and a single process interacts with Microsoft Distributed Transaction Coordinator (DTC) to handle `prepare` and `commit` transactions. This improves the performance by eliminating thread creation and destruction for every 2PC transaction.  
  
## Default Maximum Thread Settings  
 You do not have to worry about overburdening this pool unless large numbers of 2PC transactions are processed. Only when `prepare` or `commit` times for the transactions become very long can queuing to interact with DTC occur.  
  
- Default maximum threads for each CPU is 20.  
  
- Default maximum active threads for each CPU is 19.  
  
- Default maximum total threads for each system is 80.  
  
  You can adjust the default amounts by adding a TEXT string value to the registry location:  
  
  **HKLM\Software\Microsoft\Cedar\Defaults\Threads**  
  
- IOPortPoolFactor=20  
  
- IOPortActive=19  
  
- ThreadPoolMax=80  
  
### Rules for Specifying Values  
 The following rules apply for specifying values:  
  
-   All values must be greater than zero.  
  
-   IOPortPoolFactor must be >= IOPortActive + 1.  
  
-   ThreadPoolMax must be >= IOPortPoolFactor.  
  
> [!CAUTION]
>  Allocating too many threads can cause Windows to run out of resources, and that can cause unpredictable behavior in COM+ and in Windows.  
  
## See Also  
 [Transaction Programs that Run for a Long Time](../core/transaction-programs-that-run-for-a-long-time2.md)   
 [Transaction Integrator Performance Guide](../core/transaction-integrator-performance-guide1.md)