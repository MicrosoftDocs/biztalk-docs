---
title: "How to Capture a Memory Dump of a Process that is Non Responsive | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ad53376-2fab-4dee-8a6a-a44d157390f2
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Capture a Memory Dump of a Process that is Non Responsive
The BizTalk process BTSNTSvc.exe is defined as **hanging** when the process seems to stop responding. Common symptoms of a process hang include:  
  
- Orchestrations appear to stop running.  
  
- Messages aren’t being processed.  
  
- General timeout issues occur.  
  
- The BizTalk process BTSNTSvc.exe consumes an unusually high amount of CPU cycles as viewed in the **Processes** tab of **Task Manager**.  
  
  To capture a memory dump of a hanging BTSNTSvc.exe process, follow these steps.  
  
### To configure the Debug Diagnostics tool to capture a hang dump  
  
1.  Launch the Debug Diagnostics tool from **Start**, **All Programs**, **IIS Diagnostics**, **Debug Diagnostics Tools**, **Debug Diagnostics Tool 1.0**.  
  
2.  If the **Select Rule Type** dialog of the Rules Configuration Wizard is displayed, click the **Cancel** button.  
  
3.  Click the **Processes** tab of the Debug Diagnostic Tool.  
  
4.  Right click the unresponsive BTSNTSvc.exe process and select **Create Full Userdump**. By default, a memory dump of the process will be saved to the \Program Files\IIS Resources\DebugDiag\Logs\Misc directory of the local computer.  
  
## See Also  
 [How to Use Debug Diagnostics to Analyze a Memory Dump](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)