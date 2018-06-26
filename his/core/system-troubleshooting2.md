---
title: "System Troubleshooting2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0dad7411-3777-4e6b-85cf-e761df2f3b8a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# System Troubleshooting
When gathering information about system difficulties, it is best to start with information provided by the Windows Event Log and System Monitor, see [Windows Utilities](../core/windows-utilities2.md) for additional information.  
  
 Event log information is generally more straightforward to interpret than trace information; use trace information only if event logs do not provide enough details.  
  
 When you report system problems to Microsoft Customer Service and Support, a technician may ask you for trace files and other system information:  
  
- Trace files  
  
- Windows Event Logs  
  
- The current configuration file (Com.cfg)  
  
- Dump files, which may be created by [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] when a system trap (exception error) occurs  
  
- Datascope traces of protocol exchanges  
  
## See Also  
 [SNA Trace Utility Fundamentals](../core/sna-trace-utility-fundamentals1.md)