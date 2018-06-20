---
title: "Trace and Diagnostic File Location2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ddee4f9-ddd7-43d4-b1a3-d4a5db245310
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Trace and Diagnostic File Location
The following table lists the default location of files containing trace and diagnostic information:  


|                                                          File type                                                          |            Default location            | File name or file name extensions |
|-----------------------------------------------------------------------------------------------------------------------------|----------------------------------------|-----------------------------------|
| Trace files created by the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Trace application |    \Host Integration Server\Traces     |              \*.atf               |
|                                                          Log files                                                          |         \WINNT\System32\Config         |              \*.evt               |
|                                                     Configuration file                                                      | \Host Integration Server\System\Config |              com.cfg              |
|                                                       Dr. Watson file                                                       |                 \WINNT                 |           drwtsn32.log            |
|                                                         Dump files                                                          |    \Host Integration Server\Traces     |            snadump.log            |

## See Also  
 [SNA Trace Utility Fundamentals](../core/sna-trace-utility-fundamentals1.md)