---
title: "Interpreting Traces2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b92c67a-1cb7-45d5-a9e6-b08cdfd79ff8
caps.latest.revision: 3
---
# Interpreting Traces
The [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] Trace feature provides message, client API, SnaBase, Transaction Integrator, PU 2.1 node, and link service tracing.  
  
 The following table shows the information needed for interpreting each type.  
  
|Type of tracing|Software component traced|Area of expertise needed|  
|---------------------|-------------------------------|------------------------------|  
|APPC API|SNA applications|APPC programming|  
|CPI-C API|SNA applications|CPI-C programming|  
|LUA API|SNA applications|LUA programming|  
|SNA Formats|SnaServer (PU 2.1 Node)|SNA formats|  
|Data Link Control (messages)|SnaServer (PU 2.1 node) or link service|DLC interface|  
|Level 2 Messages|Link service|Link service interface|  
|3270 Messages|SNA Applications, SnaServer (PU 2.1 Node), or SnaBase|3270 emulator interface|  
|Internal Messages|All software components for Host Integration Server|Intended for product support personnel|  
|APPC Messages|SNA Applications, SnaServer (PU 2.1 Node), or SnaBase|Intended for product support personnel|  
|Internal|All software components for Host Integration Server|Intended for product support personnel|  
  
## See Also  
 [Trace Types](../core/trace-types.md)   
 [SNA Trace Utility Fundamentals](../core/sna-trace-utility-fundamentals.md)