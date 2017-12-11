---
title: "Windows CPI-C Considerations1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b34a661b-7f4f-4a0e-86ba-369434f76fd5
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Windows CPI-C Considerations
The following Common Programming Interface for Communications (CPI-C) calls and Windows extensions are of particular importance. You should review them before using [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)].  
  
> [!NOTE]
>  The names of the calls are pseudonyms. The actual C function names appear in parentheses after the pseudonym. For example, **Set_Processing_Mode** is the pseudonym for a call. The actual function name is **cmspm**.  
  
 [Set_Processing_Mode](../HIS2010/set-processing-mode-cpi-c-1.md)( **cmspm**)  
 Specifies for the conversation whether subsequent calls are returned when the operation they request is complete (blocking) or immediately after the operation is initiated (nonblocking). A program is notified of the completion of nonblocking calls when it issues **Wait_For_Conversation** or through a Windows message sent to a WndProc identified by *hwndNotify* in **Specify_Windows_Handle**. When the processing mode is set for a conversation, it applies to all subsequent calls on the conversation until the mode is set again.  
  
 [Specify_Windows_Handle](../HIS2010/specify-windows-handle-cpi-c-1.md)( **xchwnd**)  
 Sets the window handle to which a message is sent on completion of an operation in nonblocking mode.  
  
 [Wait_For_Conversation](../HIS2010/wait-for-conversation-cpi-c-2.md)( **cmwait**)  
 Waits for the completion of an operation that was initiated when theprocessing mode conversation characteristic was set to CM_NON_BLOCKING and CM_OPERATION_INCOMPLETE was returned in the *return_code* parameter. Use **Wait_For_Conversation** when running a background thread or a single-threaded application for Microsoft Windows. This most likely occurs when porting code from older versions of Host Integration Server and SNA Server.  
  
> [!IMPORTANT]
>  An application can set the processing mode by calling **Set_Processing_Mode**. If the window handle is set to NULL, or this call is never issued, the application must call **Wait_For_Conversation** to be notified when the outstanding operation completes.  
  
 When an asynchronous operation is complete, the applications window *hwndNotify* receives the message returned by **RegisterWindowMessage** with "WinAsyncCPIC" as the input string. The *wParam* value contains the conversation return code from the operation that is completing. Its values depend on which operation was originally issued. The *lParam* argument contains the CM_PTR to the conversation identifier specified in the original function call.  
  
 [WinCPICCleanup](../HIS2010/wincpiccleanup1.md)  
 Terminates and unregisters an application from a Windows CPI-C implementation.  
  
> [!IMPORTANT]
>  This function must be called by an application when finished to unregister the application from the Windows CPI-C implementation.  
  
 [WinCPICExtractEvent](../HIS2010/wincpicextractevent1.md)  
 Provides a method for an application to determine the event handle being used for a CPI-C conversation.  
  
 [WinCPICIsBlocking](../HIS2010/wincpicisblocking2.md)  
 Determines if a task is executing while waiting for a previous blocking call to finish. This was used when Windows version 3.*x* went into a **PeekMessageLoop** while allowing Windows to continue. Although a call issued on a blocking function appears to an application as though it blocks, the Windows CPI-C dynamic-link library (DLL) has to relinquish the processor to allow other applications to run. This means that it is possible for the application that issued the blocking call to be re-entered, depending on the messages it receives. In this instance, **WinCPICIsBlocking** can be used to determine whether the application task currently has been re-entered while waiting for an outstanding blocking call to finish.  
  
 This extension is intended to provide help to an application written to use the CM_BLOCKING characteristic of the Windows **Specify_Processing_Mode** function. **WinCPICIsBlocking** serves the same purpose as **InSendMessage** in the Windows API.  
  
 Older applications that were originally targeted at Windows version 3.*x* and that support multiple conversations must specify CM_NONBLOCKING in **Specify_Processing_Mode** so they can support multiple outstanding operations simultaneously. Applications are still limited to one outstanding operation per conversation in all environments.  
  
> [!NOTE]
>  Windows CPI-C prohibits more than one outstanding blocking call per thread.  
  
 [WinCPICSetBlockingHook](../HIS2010/wincpicsetblockinghook1.md)  
 Allows a Windows CPI-C implementation to block CPI-C function calls by means of a new function. Blocking calls apply only if you do not use asynchronous calls. If a function needs to block, the blocking call is called repeatedly until the original request completes. This allows Windows to continue to run while the original application waits for the call to return. Note that while inside the blocking call, the application can be re-entered. **WinCPICSetBlockingHook** was used by Windows version 3.*x* applications that went into a **PeekMessageLoop** to make blocking calls without blocking the rest of the system.  
  
> [!NOTE]
>  By default, Windows Server does not go into a **PeekMessageLoop**. Rather, they block an event waiting for the call to complete. The only time you need to use **WinCPICSetBlockingHook** for Windows is when a single-threaded application for Windows shares common source code. In this case, you must explicitly make this call. Contrast this call with **WinCPICIsBlocking** and **WinCPICUnhookBlockingHook**.  
  
 [WinCPICSetEvent](../HIS2010/wincpicsetevent2.md)  
 Associates a Win32 event handle with a verb completion.  
  
 [WinCPICStartup](../HIS2010/wincpicstartup1.md)  
 Allows an application to specify the version of Windows CPI-C required and to retrieve details of the specific CPI-C implementation.  
  
> [!IMPORTANT]
>  An application must call this function to register itself with a Windows CPI-C implementation before issuing any further Windows CPI-C calls.  
  
 [WinCPICUnhookBlockingHook](../HIS2010/wincpicunhookblockinghook1.md)  
 Removes any previous blocking hook that has been installed and reinstalls the default blocking mechanism.