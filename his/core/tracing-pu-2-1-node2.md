---
title: "Tracing PU 2.1 Node2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19d59f2a-fad8-4003-a08a-b8e46428a4c6
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Tracing PU 2.1 Node
The following table details PU 2.1 Node traces.  


|   Trace option    |                                                                                        Activity traced for the SnaServer (PU 2.1 node).                                                                                         |
|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Internal Messages |                                                                                Messages between the SnaServer (PU 2.1 node) and the SNA Manager.                                                                                |
|   3270 Messages   |                                                              Messages between the PU 2.1 node and all 3270 client computers (3270 emulators and/or LUA programs).                                                               |
| Data Link Control |                                                                                       Messages between the PU 2.1 node and link services.                                                                                       |
|    SNA Formats    | Data link control messages that are in [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] formats. Understanding such messages requires knowledge of Host Integration Server formats and protocols. |
|  LU 6.2 Messages  |                                                                                       Messages between the PU 2.1 node and the APPC DLL.                                                                                        |

## See Also  
 [Tracing SNA APIs](../core/tracing-sna-apis2.md)   
 [Tracing SnaBase](../core/tracing-snabase2.md)   
 [Tracing Link Services](../core/tracing-link-services1.md)   
 [Tracing for TN3270](../core/tracing-for-tn32702.md)   
 [Tracing for TN5250](../core/tracing-for-tn52501.md)   
 [Tracing Servers Components](../core/tracing-servers-components2.md)