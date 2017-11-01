---
title: "Optimizing Communications2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21b6852e-efa3-4384-b273-695633ed7723
caps.latest.revision: 3
---
# Optimizing Communications
Servers used primarily for communications need to provide fast throughput, but they do not need to provide fast file access (as a file server would). Faster throughput will result if portions of memory are set aside for communications programs (such as Host Integration Server or Microsoft® SQL Server).  
  
 Such dedicated memory includes nonpaged memory, or portions of memory that are never swapped to disk, but remain available for immediate use at all times. If more memory is dedicated to Host Integration Server or similar programs, less memory is available for file sharing.  
  
 Windows Server allows you to view or change network throughput options. However, Host Integration Server installation automatically sets the option to maximize throughput for network applications.  
  
 Servers used primarily for communications run many important background processes (processes not related to user actions in the current window). These servers generally do not need to run foreground processes at maximum speed. Host Integration Server throughput can be increased by making the operating system more responsive to background processes and less responsive to foreground processes.  
  
 A server that is less responsive to foreground processes will run local applications such as word-processing software, spreadsheets, or SNA Manager more slowly. Tasking is most appropriate for servers used primarily to support client systems, and not for servers used locally as desktop computers.  
  
### To optimize background processing for a computer running Windows  
  
1.  Click **Start**, point to **Settings**,click **Control Panel**, and then double-click **System**.  
  
2.  Select the **Advanced** tab.  
  
3.  In the **Performance** box, click **Performance Options**.  
  
4.  In the **Application response** box, **select Applications or Background services**.  
  
5.  Click **OK**, and then click **OK** again.  
  
## See Also  
 [Transaction Programs](../core/transaction-programs.md)   
 [Understanding Connectivity](../core/understanding-connectivity.md)