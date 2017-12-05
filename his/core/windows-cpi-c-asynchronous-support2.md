---
title: "Windows CPI-C Asynchronous Support2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7bdad0c4-3be5-465d-a8ca-86fc9286f241
caps.latest.revision: 4
---
# Windows CPI-C Asynchronous Support
A program that issues a call and does not regain control until the call completes cannot perform any other operations. This type of operation, referred to as blocking, is not suited to a server application designed to handle multiple requests from many clients. Asynchronous call completion returns the initial call immediately, so the application can continue with other processes.  
  
 Windows Common Programming Interface for Communications (CPI-C) support is related to asynchronous communications and includes the following calls and extensions:  
  
 [Set_Processing_Mode (CPI-C)](../core/set-processing-mode-cpi-c-1.md)  
  
 [Specify_Windows_Handle (CPI-C)](../core/specify-windows-handle-cpi-c-1.md)  
  
 [Wait_For_Conversation (CPI-C)](../core/wait-for-conversation-cpi-c-2.md)  
  
 [WinCPICExtractEvent](../core/wincpicextractevent1.md)  
  
 [WinCPICIsBlocking](../core/wincpicisblocking2.md)  
  
 [WinCPICSetBlockingHook](../core/wincpicsetblockinghook1.md)  
  
 [WinCPICSetEvent](../core/wincpicsetevent2.md)  
  
 [WinCPICUnhookBlockingHook](../core/wincpicunhookblockinghook1.md)  
  
 Two methods under Microsoft Windows are available for asynchronous verb completion:  
  
-   Message posting using window handles.  
  
-   Waiting for Win32 events.  
  
 The traditional method uses messages posted to a window handle to notify an application of verb completion. This method was used in earlier versions of the product to support Windows 3.*x*.  
  
 Asynchronous support using message posting is appended to the [Set_Processing_Mode (CPI-C)](../core/set-processing-mode-cpi-c-1.md) call and enables an application to be notified of call completion on a window handle. Calling **RegisterWindowsMessage** with "WinAsyncCPIC" as the string, an application passes a window handle by which the application is notified of call completion. The application then makes the CPI-C call, and when it completes a message is posted to the window handle that was passed, notifying the application that the call is complete.  
  
 With the exception of an asynchronous [Receive](../core/receive-cpi-c-1.md) call that can issue certain other calls while pending, a conversation can have only one incomplete operation at any time. For more information about using an asynchronous **Receive** call, see [Using Asynchronous Call Completion](../core/asynchronous-call-completion2.md). In the case of an incomplete operation, the program can issue [Wait_For_Conversation](../core/wait-for-conversation-cpi-c-2.md) to test for its completion or [Cancel_Conversation](../core/cancel-conversation-cpi-c-1.md) to end the conversation and the incomplete operation.  
  
 A second method using Win32 events for notification is supported in [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)].  
  
 If an event has been registered with the conversation using **WinCPICSetEvent**, an application can call the Win32 **WaitForSingleObject** or **WaitForMultipleObjects** function to wait to be notified of the completion of the verb.  
  
 The only Windows extension functions required for Windows CPI-C are for initialization ([WinCPICStartup](../core/wincpicstartup1.md)) and termination ([WinCPICCleanup](../core/wincpiccleanup1.md)) purposes. Depending on your application, other Windows extensions for handling asynchronous verb completion can be useful, but they are not required. For an example of how to use Windows CPI-C asynchronous calls and Windows extensions, see [Asynchronous Call Completion](../core/asynchronous-call-completion2.md). For a complete description of all Windows CPI-C calls and extensions, see [CPI-C Calls](../core/cpi-c-calls1.md) and [Extensions for the Windows Environment](../core/extensions-for-the-windows-environment2.md).