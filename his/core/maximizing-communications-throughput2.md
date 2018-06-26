---
title: "Maximizing Communications Throughput2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 77b662e5-4a55-4408-acd1-91485d64ae5c
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Maximizing Communications Throughput
Servers used primarily for communications need to provide fast throughput, but do not need to provide fast file access as a file server would. Faster throughput will result if portions of memory are set aside for communications programs such as [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] or Microsoft SQL Server.  
  
 Such dedicated memory includes nonpaged memory, or portions of memory that are never switched to disk, but remain available for immediate use at all times. This helps support fast throughput. If more memory is dedicated to [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] or similar programs, less memory is available for file sharing.  
  
 With Windows operating systems, you can view or change network throughput options. For Host Integration Server, you may not need to change the throughput option. Setup automatically sets the option to maximize throughput for network applications.  
  
 Servers used primarily for communications run many important background processes. Background processes are processes not related to user actions in the current window. These servers generally do not need to run foreground processes at maximum speed. Therefore, making the operating system more responsive to background processes and somewhat less responsive to foreground processes can increase Host Integration Server throughput. Setting background or foreground responsiveness is known as tasking.  
  
 A server that is less responsive to foreground processes will run local applications such as word processing software, spreadsheets, or the SNA Manager more slowly. Tasking is most appropriate for servers used primarily to support client computers, not servers used locally as desktop computers.  
  
 The options available for tasking are:  
  
- Best Foreground Application Response Time  
  
- Foreground Application More Responsive than Background  
  
- Foreground and Background Applications Equally Responsive  
  
  Choose the one that is best suited to your network configuration.  
  
## See Also  
 [System Monitor Overview](../core/system-monitor-overview1.md)   
 [System Monitor](../core/system-monitor1.md)