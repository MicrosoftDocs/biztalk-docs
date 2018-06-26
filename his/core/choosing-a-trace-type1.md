---
title: "Choosing a Trace Type1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c10c309c-147e-4b15-ab1a-5eafbe014770
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Choosing a Trace Type
After selecting one or more [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] components to be traced, decide the type of tracing to apply.  

 The following table describes the types of tracing available:  


| Type of tracing |                                                                                          Activity traced                                                                                          |                       Applies to installed components                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
|   Internal\*    |                                      Activity within a software component of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)].                                      | SnaBase, SnaServer (PU 2.1 node), SNA applications, link services and more. |
|     Message     | Messages passed into and out of a software component of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)], including messages sent to and received from the network. | SnaBase, SnaServer (PU 2.1 node), SNA applications, link services and more. |
|       API       |    Information passed into and out of a [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] DLL, as the DLL communicates with an application, such as the APPC DLL.    |                         SNA applications and more.                          |

 \* Internal tracing is intended for use by product support technicians. Interpreting internal traces and certain types of message traces requires a specialized knowledge base.  

## See Also  
 [SNA Trace Utility Fundamentals](../core/sna-trace-utility-fundamentals1.md)