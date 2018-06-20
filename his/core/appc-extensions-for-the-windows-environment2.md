---
title: "APPC Extensions for the Windows Environment2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13212873-293f-4fbf-a192-87b9cf945e7e
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# APPC Extensions for the Windows Environment
This section describes API extensions to Windows Advanced Program-to-Program Communications (APPC) that allow asynchronous communication. Asynchronous communication occurs when a function returns before the request completes. The application is notified later when the request is completed.  
  
 Under Microsoft® Windows®, three methods are available for asynchronous communication using the APPC API:  
  
- Message posting using window handles.  
  
- Waiting on Win32® events.  
  
- Using Win32 I/O completion ports.  
  
  The first method uses messages posted to a window handle to notify an application of verb completion. This method using window handles and messages was supported on Microsoft Windows 3.x. There is one such window for each APPC application, independent of the number of conversations. Each APPC conversation can have one asynchronous verb outstanding at any time. When a verb completes, the posting to the window takes as parameters the asynchronous task handle returned by the original call and a pointer to the verb control block which has completed, containing the return codes of the verb.  
  
  The extensions using window handles and message posting described in this section ([WinAsyncAPPC](../core/winasyncappc1.md)) were designed for all implementations and versions of Microsoft Windows from version 3.0 through the latest versions of Windows. They provided compatibility for Windows programming and optimum application performance in the 16-bit Windows operating environment.  
  
  A second method using Win32 events for notification is supported. The extensions using Win32 events described in this section ([WinAsyncAPPCEx](../core/winasyncappcex1.md)) operate only on Windows, and offer optimum application performance in the 32-bit Windows operating environment. If an event has been registered with the conversation, then an application can call the Win32 **WaitForSingleObject** or **WaitForMultipleObjects** function to wait to be notified of the completion of the verb.  
  
  A third method using Win32 I/O completion ports for notification is supported on Windows. The extensions using I/O completion ports described in this section ([WinAsyncAPPCIOCP](../core/winasyncappciocp2.md)) operate only on Windows, and offer optimum application performance in the 32-bit Windows operating environment. If an I/O completion port has been created using **CreateIoCompletionPort**, then an application can call the Win32 **GetQueuedCompletionStatus** function to wait to be notified of the completion of the verb.  
  
  Windows APPC allows multithreaded Windows-based processes. A process contains one or more threads of execution. All references to threads in this document refer to actual threads in multithreaded Windows environments.  
  
  This section provides, for each extension, a definition of the function, syntax, returns, and remarks for using the function.  
  
## In This Section  
  
-   [WinAsyncAPPC](../core/winasyncappc1.md)  
  
-   [WinAsyncAPPCEx](../core/winasyncappcex1.md)  
  
-   [WinAsyncAPPCIOCP](../core/winasyncappciocp2.md)  
  
-   [WinAPPCCancelAsyncRequest](../core/winappccancelasyncrequest2.md)  
  
-   [WinAPPCCancelBlockingCall](../core/winappccancelblockingcall1.md)  
  
-   [WinAPPCCleanup](../core/winappccleanup1.md)  
  
-   [WinAPPCIsBlocking](../core/winappcisblocking1.md)  
  
-   [WinAPPCStartup](../core/winappcstartup1.md)  
  
-   [WinAPPCSetBlockingHook](../core/winappcsetblockinghook1.md)  
  
-   [WinAPPCUnhookBlockingHook](../core/winappcunhookblockinghook2.md)