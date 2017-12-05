---
title: "Method Calls per Second1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bbf87424-ab7d-4005-b798-5df213bf561b
caps.latest.revision: 3
---
# Method Calls per Second
The counter reports the method call volume going through the Transaction Integrator (TI) server. There are actually three counters implemented:  
  
-   Method calls using the CICS LINK mode.  
  
-   Method calls using the CICS non-LINK or calls to IMS.  
  
-   Total method calls.  
  
 Assuming that the system is in somewhat stable condition, that is, the calls are returning at the same rate that they are made, these counters represent the transactions per second throughput number for TI.  
  
## See Also  
 [Performance Monitoring Counters](../HIS2010/performance-monitoring-counters1.md)