---
description: "Learn more about: How to Capture a Memory Dump of a Process that is Leaking Memory"
title: "How to Capture a Memory Dump of a Process that is Leaking Memory"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Capture a Memory Dump of a Process that is Leaking Memory
The BizTalk process BTSNTSvc.exe is defined as having a memory leak when it fails to release memory that it no longer needs, thereby reducing the amount of available memory over time. The memory usage of the process can be determined by viewing the value under the **Mem Usage** column of the **Processes** tab available in **Task Manager**. If the process continues to consume memory over time without releasing memory then overall system performance will be adversely impacted.  
  
 This topic contains instructions for capturing a memory dump of a BizTalk process that is suspected of leaking memory by using a Rule or by manually capturing the memory dump. Use the manual method of capturing a memory dump if the occurrence of the memory leak is not predictable.  
  
### To capture a memory dump of a process that is leaking memory by using a rule  
  
1.  Launch the Debug Diagnostics tool from **Start**, **All Programs**, **IIS Diagnostics**, **Debug Diagnostics Tools**, **Debug Diagnostics Tool 1.0**.  
  
2.  If the **Select Rule Type** dialog of the Add Rule Wizard is not displayed, click the **Tools** menu, select **Rule Actions**, and click **Add Rule** to display the Add Rule Wizard.  
  
3.  Select the **Memory and Handle Leak** option in the **Select Rule Type** dialog and click **Next**.  
  
4.  Select the BTSNTSvc.exe process that is suspected of leaking memory and click **Next**.  
  
5.  In the **Configure Tracking Duration** dialog follow these steps:  
  
    1.  If the observed process memory growth occurs immediately, check the option to **Start memory tracking immediately when rule is activated**. If the observed process memory growth doesn't occur immediately, specify an appropriate number of minutes in the **Warm-up time** text box after which memory tracking will start.  
  
        > [!NOTE]
        >  The observed process memory growth may not occur immediately if the memory leak is caused when loading a particular component into memory, for example when a BizTalk orchestration references an external component.  
  
    2.  Specify an appropriate number of minutes in the **Tracking time** text box after which memory tracking will stop. This should be a number of minutes long enough to reproduce the memory leak. A memory dump of the process will be captured after this time period has elapsed.  
  
    3.  Check the option to **Auto-create a crash rule to get userdump on unexpected process exit**.  
  
    4.  Click **Next**.  
  
6.  In the **Select Dump Location And Rule Name** dialog click **Next** to accept the default values.  
  
7.  In the **Rule Completed** dialog click **Finish** to accept the default value of **Activate the rule now**.  
  
8.  By default, a memory dump of the process will be saved to the \Program Files\IIS Resources\DebugDiag\Logs\\<*name of crash rule*\> directory of the local computer after the time intervals specified in the **Configure Tracking Duration** dialog has elapsed.  
  
### To manually capture a memory dump of a process that is leaking memory  
  
1.  Launch the Debug Diagnostics tool from **Start**, **All Programs**, **IIS Diagnostics**, **Debug Diagnostics Tools**, **Debug Diagnostics Tool 1.0**.  
  
2.  If the **Select Rule Type** dialog of the Add Rule Wizard is displayed, click **Cancel**.  
  
3.  Click to select the **Processes** tab of the Debug Diagnostic Tool.  
  
4.  Right-click the BTSNTSvc.exe process that is suspected of leaking memory and click **Monitor For Leaks**.  
  
5.  Monitor the memory usage of the process in **Task Manager** and when the memory usage of the process approaches 60-80% of the memory available on the BizTalk computer; manually capture a memory dump of the process by right-clicking the process and selecting the option to **Create Full Userdump**.  
  
6.  By default, a memory dump of the process will be saved to the \Program Files\IIS Resources\DebugDiag\Logs\Misc\ directory of the local computer.  
  
## See Also  
 [How to Use Debug Diagnostics to Analyze a Memory Dump](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)
