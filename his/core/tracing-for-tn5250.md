---
title: "Tracing for TN52501 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: de49e4a2-4146-4f76-83db-2fab7d78ed10
caps.latest.revision: 3
---
# Tracing for TN5250
You can enable or disable tracing for TN5250 using the [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] Trace application. Host Integration Server Trace provides API, internal, and message tracing.  
  
 The Host Integration Server Trace application places trace files for TN5250 in the \Host Integration Server\Tracesfolder by default.  
  
 The following table illustrates the TN5250 file names used by Host Integration Server Trace:  
  
|Service|Type of tracing|File names used|File names used|  
|-------------|---------------------|---------------------|---------------------|  
|TN5250|API|Tn5api1.atf|Tn5api2.atf|  
||Message|Tn5msG1.atf|Tn5msg2.atf|  
||Internal|Tn5int1.atf|Tn5int2.atf|  
  
## See Also  
 [Tracing SNA APIs](../core/tracing-sna-apis.md)   
 [Tracing SnaBase](../core/tracing-snabase.md)   
 [Tracing PU 2.1 Node](../core/tracing-pu-2-1-node.md)   
 [Tracing Link Services](../core/tracing-link-services.md)   
 [Tracing for TN3270](../core/tracing-for-tn3270.md)   
 [Tracing Servers Components](../core/tracing-servers-components.md)