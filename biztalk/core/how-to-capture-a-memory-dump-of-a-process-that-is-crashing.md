---
description: "Learn more about: How to Capture a Memory Dump of a Process that is Crashing"
title: "How to Capture a Memory Dump of a Process that is Crashing"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Capture a Memory Dump of a Process that is Crashing
The BizTalk process BTSNTSvc.exe is defined as **crashing** when the process is unexpectedly terminated by Windows. A crash is typically caused by an unhandled exception in the process such as an access violation or a stack overflow. In these situations, the Windows default debugger, Dr. Watson (drwtsn32.exe) catches the exception and terminates the process.  
  
 To capture a memory dump of a process that is crashing, configure the Debug Diagnostics tool to catch the unhandled exception by following these steps:  
  
### To configure the Debug Diagnostics tool to capture a crash dump  
  
1.  Launch the Debug Diagnostics tool from **Start**, **All Programs**, **IIS Diagnostics**, **Debug Diagnostics Tools**, **Debug Diagnostics Tool 1.0**.  
  
2.  If the **Select Rule Type** dialog of the Add Rule Wizard is not displayed, click the **Tools** menu, select **Rule Actions**, and click **Add Rule** to display the Add Rule Wizard.  
  
3.  Select the **Crash** option in the **Select Rule Type** dialog and click **Next**.  
  
4.  Select **A specific process** in the **Select Target Type** dialog and click **Next**.  
  
5.  Select the BTSNTSvc.exe process that is crashing and click **Next**.  
  
6.  In the **Advanced Configuration** dialog click **Next** to accept the default values.  
  
7.  In the **Select Dump Location And Rule Name** dialog click **Next** to accept the default values.  
  
8.  In the **Rule Completed** dialog click **Finish** to accept the default value of **Activate the rule now**.  
  
9. By default, a memory dump of the process will be saved to the \Program Files\IIS Resources\DebugDiag\Logs\\<*name of crash rule*\> directory of the local computer the next time that an unhandled exception occurs in the process.  
  
## See Also  
 [How to Use Debug Diagnostics to Analyze a Memory Dump](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)
