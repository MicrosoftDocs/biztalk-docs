---
title: "Maximizing Communications Performance1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df8c16a8-4b38-4453-9558-1a00a6ec6695
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Maximizing Communications Performance
Servers used primarily for communications need to provide fast network performance, but do not need to provide fast file access (such as a server used primarily as a file server). Faster network communication can be achieved if portions of memory are set aside for communications by configuring "nonpaged memory". Nonpaged memory is portions of memory that are never swapped to disk, but remain available for immediate use at all times.  
  
 In Windows, you can view or change network performance options, as described in the following procedures. For a [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer, you may not need to change this option, because Host Integration Server Setup automatically sets the option to maximize throughput for network applications.  
  
### To view or change network communication options for a Windows Server  
  
1. Click **Start**, point to **Settings**, click **Control Panel**, and then double-click **Network and Dial-up Connections**.  
  
2. Double-click **Local Area Connection** and click **Properties**.  
  
3. Click **File and Printer Sharing for Microsoft Network**, and click **Properties**.  
  
4. For a server dedicated to communications, select **Maximize data throughput for network applications**.  
  
5. Click **OK**, and then click **OK** again. Click **Close**.  
  
   If you made a change, the **Network Settings Change** message box appears. To put the changes into effect right away, restart the computer. To put the changes into effect later (at next startup), do not restart the computer now.