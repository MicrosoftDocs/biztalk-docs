---
description: "Learn more about: Diagnose Problems with Trace"
title: "Diagnose Problems with Trace1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Diagnose Problems with Trace
The following table shows examples of possible difficulties and the types of tracing that may be useful.  


|                                                Problem                                                 |                                                                            What to trace                                                                             |
|--------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] cannot connect to host. |                                             For the SnaServer (PU 2.1 node), trace data link control and 3270 Messages.                                              |
|                       SNA Manager does not reflect changes in network services.                        |                                 For the SnaServer (PU 2.1 node), trace Internal Messages; for Manage Agent, enable internal tracing.                                 |
|          Windows-based client computer cannot connect to a Host Integration Server resource.           | For any client computer, enable internal tracing For a 3270 or LUA client computer, trace 3270 messages For an APPC or CPI-C client computer, trace LU 6.2 messages. |

## See Also  
 [SNA Trace Utility Fundamentals](../core/sna-trace-utility-fundamentals1.md)
