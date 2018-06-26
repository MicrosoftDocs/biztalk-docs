---
title: "Extensions for the Windows Environment1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b3c23a9-00d3-4864-835b-2074175791b5
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Extensions for the Windows Environment
This section describes API extensions to Microsoft® Windows® Common Programming Interface for Communications (CPI-C) that allow nonblocking or asynchronous verb completion. Asynchronous verbs return control to the program immediately, without waiting for full execution, and must notify the application later when the verb has been completed. An application is also notified in response to the completion of a [Wait_For_Conversation](../core/wait-for-conversation-cpi-c-1.md) call. In contrast, synchronous verbs block, that is, the function call does not return until the call has completed.  
  
 Under Microsoft® Windows Server, two methods are available for handling asynchronous verb completion:  
  
- Message posting using window handles.  
  
- Waiting on Win32® events.  
  
  The first method uses messages posted to a window handle to notify an application of verb completion. There is one such window for each CPI-C application. Each CPI-C conversation can have one asynchronous verb outstanding at any time. When a verb completes, the posting to the window takes as parameters the CPI-C conversation identifier of the verb that has completed, and the return code of the verb.  
  
> [!NOTE]
>  The extensions using window handles and message posting described in this section were designed for all implementations and versions of Microsoft Windows. They are now supported only for Windows.  
  
 A second method using Win32 events for notification is supported on Microsoft® Host Integration Server. The extensions using Win32 events described in this section ([WinCPICSetEvent](../core/wincpicsetevent1.md) and [WinCPICExtractEvent](../core/wincpicextractevent2.md))operate only on Windows Server and offer the optimum application performance in the 32-bit operating environment. If an event has been registered with the conversation, an application can call the Win32 **WaitForSingleObject** or **WaitForMultipleObjects** function to wait to be notified of the completion of the verb.  
  
 Windows CPI-C allows multithreaded Windows-based processes. Multithreading is the running of several processes in rapid sequence within a single program. A process contains one or more threads of execution.  
  
 The extension descriptions in this section provide a definition of the function, syntax, return values, and remarks for using these Windows extensions in CPI-C programs.  
  
## In This Section  
  
-   [WinCPICCleanup](../core/wincpiccleanup2.md)  
  
-   [WinCPICExtractEvent](../core/wincpicextractevent2.md)  
  
-   [WinCPICIsBlocking](../core/wincpicisblocking1.md)  
  
-   [WinCPICSetBlockingHook](../core/wincpicsetblockinghook2.md)  
  
-   [WinCPICSetEvent](../core/wincpicsetevent1.md)  
  
-   [WinCPICStartup](../core/wincpicstartup2.md)  
  
-   [WinCPICUnhookBlockingHook](../core/wincpicunhookblockinghook2.md)