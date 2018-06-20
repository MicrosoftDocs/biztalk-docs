---
title: "Method Calls per Second2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2aa4570e-9a87-4aea-b66b-7c9ea293bfb2
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Method Calls per Second
The counter reports the method call volume going through the Transaction Integrator (TI) server. There are actually three counters implemented:  
  
- Method calls using the CICS LINK mode.  
  
- Method calls using the CICS non-LINK or calls to IMS.  
  
- Total method calls.  
  
  Assuming that the system is in somewhat stable condition, that is, the calls are returning at the same rate that they are made, these counters represent the transactions per second throughput number for TI.  
  
## See Also  
 [Performance Monitoring Counters](../core/performance-monitoring-counters2.md)