---
description: "Learn more about: Tracing for TN3270"
title: "Tracing for TN32702"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Tracing for TN3270
You can enable or disable tracing for TN3270 using the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Trace application. [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Trace provides API, internal, and message tracing.  
  
 [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] SNA Trace Utility places trace files for TN3270 in the \Host Integration Server\Tracesfolder by default.  
  
 The following table illustrates the TN3270 file names used by [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Trace:  
  
|Service|Type of tracing|File names used|File names used|  
|-------------|---------------------|---------------------|---------------------|  
|TN3270|API|Tn3api1.atf|Tn3api2.atf|  
||Internal|Tn3int1.atf|Tn3int2.atf|  
||Message|Tn3msg1.atf|Tn3imsg2.atf|  
||TN3270 internal trace|Tn_00.atf – Tn0a.atf||  
  
> [!NOTE]
>  The TN3270 internal trace contains up to 1024 bytes of information and creates up to ten files. The names are Tn_00.atf to Tn_0a.atf.  
  
> [!NOTE]
>  SNA Trace event monitoring will not stop the TN3270 internal trace.  
  
## See Also  
 [Tracing SNA APIs](../core/tracing-sna-apis2.md)   
 [Tracing SnaBase](../core/tracing-snabase2.md)   
 [Tracing PU 2.1 Node](../core/tracing-pu-2-1-node2.md)   
 [Tracing Link Services](../core/tracing-link-services1.md)   
 [Tracing for TN5250](../core/tracing-for-tn52501.md)   
 [Tracing Servers Components](../core/tracing-servers-components2.md)
