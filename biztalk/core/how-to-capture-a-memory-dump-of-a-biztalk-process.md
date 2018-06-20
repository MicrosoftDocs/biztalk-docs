---
title: "How to Capture a Memory Dump of a BizTalk Process | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8053fcf3-b331-4245-b3c3-21290463e0c0
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Capture a Memory Dump of a BizTalk Process
Under certain circumstances it may be necessary to capture a memory dump of a process running on a BizTalk Server to perform an in depth analysis of the process. Situations that may require analysis of a memory dump include the following:  
  
- When a process is unresponsive.  
  
- When a process is crashing.  
  
- When a process leaks memory.  
  
  This section includes the steps that should be followed to capture the appropriate type of memory dump.  
  
## Installation of the IIS Diagnostics Toolkit  
 Each of the topics in this section requires the use of the **Debug Diagnostics Tool** of the IIS Diagnostics Toolkit to capture a memory dump. To install the **Debug Diagnostics Tool** of the IIS Diagnostics Toolkit follow these steps:  
  
1.  Download the IIS Diagnostics Toolkit from [Internet Information Services Diagnostic Tools](http://go.microsoft.com/fwlink/?LinkId=64426).  
  
2.  Double-click the **iisdiag.msi** package to start the IIS Diagnostics Toolkit setup program and choose the **Custom** setup type.  
  
3.  In the **Custom Setup** dialog, ensure that the option for the **Debug Diagnostics Tool 1.0** is enabled and complete the steps in the setup program.  
  
## In This Section  
  
-   [How to Capture a Memory Dump of a Process that is Non Responsive](../core/how-to-capture-a-memory-dump-of-a-process-that-is-non-responsive.md)  
  
-   [How to Capture a Memory Dump of a Process that is Crashing](../core/how-to-capture-a-memory-dump-of-a-process-that-is-crashing.md)  
  
-   [How to Capture a Memory Dump of a Process that is Leaking Memory](../core/how-to-capture-a-memory-dump-of-a-process-that-is-leaking-memory.md)  
  
-   [How to Use Debug Diagnostics to Analyze a Memory Dump](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)