---
title: "Windows CPI-C Asynchronous Support1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c84ff0b-205a-4578-b8e7-82283ebe8d40
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Windows CPI-C Asynchronous Support
A program that issues a call and does not regain control until the call completes cannot perform any other operations. This type of operation, referred to as blocking, is not suited to a server application designed to handle multiple requests from many clients. Asynchronous call completion returns the initial call immediately, so the application can continue with other processes.  
  
 Windows Common Programming Interface for Communications (CPI-C) support is related to asynchronous communications and includes the following calls and extensions:  
  
 [Set_Processing_Mode (CPI-C)](../HIS2010/set-processing-mode-cpi-c-1.md)  
  
 [Specify_Windows_Handle (CPI-C)](../HIS2010/specify-windows-handle-cpi-c-1.md)  
  
 [Wait_For_Conversation (CPI-C)](../HIS2010/wait-for-conversation-cpi-c-2.md)  
  
 [WinCPICExtractEvent](../HIS2010/wincpicextractevent1.md)  
  
 [WinCPICIsBlocking](../HIS2010/wincpicisblocking2.md)  
  
 [WinCPICSetBlockingHook](../HIS2010/wincpicsetblockinghook1.md)  
  
 [WinCPICSetEvent](../HIS2010/wincpicsetevent2.md)  
  
 [WinCPICUnhookBlockingHook](../HIS2010/wincpicunhookblockinghook1.md)  
  
 Two methods under Microsoft Windows are available for asynchronous verb completion:  
  
-   Message posting using window handles.  
  
-   Waiting for Win32 events.  
  
 The traditional method uses messages posted to a window handle to notify an application of verb completion. This method was used in earlier versions of the product to support Windows 3.*x*.  
  
 Asynchronous support using message posting is appended to the [Set_Processing_Mode (CPI-C)](../HIS2010/set-processing-mode-cpi-c-1.md) call and enables an application to be notified of call completion on a window handle. Calling **RegisterWindowsMessage** with "WinAsyncCPIC" as the string, an application passes a window handle by which the application is notified of call completion. The application then makes the CPI-C call, and when it completes a message is posted to the window handle that was passed, notifying the application that the call is complete.  
  
 With the exception of an asynchronous [Receive](../HIS2010/receive-cpi-c-1.md) call that can issue certain other calls while pending, a conversation can have only one incomplete operation at any time. For more information about using an asynchronous **Receive** call, see [Using Asynchronous Call Completion](../core/asynchronous-call-completion1.md). In the case of an incomplete operation, the program can issue [Wait_For_Conversation](../HIS2010/wait-for-conversation-cpi-c-2.md) to test for its completion or [Cancel_Conversation](../HIS2010/cancel-conversation-cpi-c-1.md) to end the conversation and the incomplete operation.  
  
 A second method using Win32 events for notification is supported in [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)].  
  
 If an event has been registered with the conversation using **WinCPICSetEvent**, an application can call the Win32 **WaitForSingleObject** or **WaitForMultipleObjects** function to wait to be notified of the completion of the verb.  
  
 The only Windows extension functions required for Windows CPI-C are for initialization ([WinCPICStartup](../HIS2010/wincpicstartup1.md)) and termination ([WinCPICCleanup](../HIS2010/wincpiccleanup1.md)) purposes. Depending on your application, other Windows extensions for handling asynchronous verb completion can be useful, but they are not required. For an example of how to use Windows CPI-C asynchronous calls and Windows extensions, see [Asynchronous Call Completion](../core/asynchronous-call-completion1.md). For a complete description of all Windows CPI-C calls and extensions, see [CPI-C Calls](../HIS2010/cpi-c-calls1.md) and [Extensions for the Windows Environment](../HIS2010/extensions-for-the-windows-environment2.md).