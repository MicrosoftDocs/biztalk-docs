---
title: "Tracing for TN32701 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc57877c-3839-4c88-aa82-9eaf72bccb06
caps.latest.revision: 4
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
 [Tracing SNA APIs](../HIS2010/tracing-sna-apis1.md)   
 [Tracing SnaBase](../HIS2010/tracing-snabase1.md)   
 [Tracing PU 2.1 Node](../HIS2010/tracing-pu-2-1-node1.md)   
 [Tracing Link Services](../HIS2010/tracing-link-services2.md)   
 [Tracing for TN5250](../HIS2010/tracing-for-tn52502.md)   
 [Tracing Servers Components](../HIS2010/tracing-servers-components1.md)