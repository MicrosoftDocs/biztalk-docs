---
title: "CPI-C Considerations for Windows2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 64eaf87a-824c-4a46-b39c-332033956348
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# CPI-C Considerations for Windows
This topic summarizes information you should keep in mind when you develop programs based on Windows operating systems.  
  
 *Asynchronous completion notification using message posting*  
 When an asynchronous operation is complete, the applications window *hwndNotify* receives the message returned by **RegisterWindowMessage** with "WinAsyncCPIC" as the input string. The *wParam* value contains the *conversation_return_code* from the operation that is completing. Its values depend on which operation was originally issued. The *IParam* argument contains the CM_PTR to the *conversation_ID* specified in the original function call.  
  
 *Asynchronous completion notification using Win32*®  *events*  
 When a verb is issued on a nonblocking conversation, it returns CM_OPERATION_INCOMPLETE if it is going to complete asynchronously. If an event has been registered with the conversation, the application can call **WaitForSingleObject** or **WaitForMultipleObjects** to be notified of the completion of the verb. [WinCPICExtractEvent](./wincpicextractevent2.md) allows a Common Programming Interface for Communications (CPI-C) applicationto determine this event handle. After the verb has completed, the application must call [Wait_For_Conversation](./wait-for-conversation-cpi-c-1.md)to determine the return code for the asynchronous verb. The [Cancel_Conversation](./cancel-conversation-cpi-c-2.md)function can be called to cancel an operation and the conversation itself.  
  
 It is the responsibility of the application to reset the event, as it is with other APIs.  
  
 If no event has been registered, the asynchronous verb completes as it does at present, which is by posting a message to the window that the application has registered with the CPI-C library.  
  
 *Byte ordering*  
 By default, Intel-byte ordering is used. For inline environments, defining NON_INTEL_BYTE_ORDER does all the required flipping for constants. Nonconstant input parameters in verb control blocks (VCBs)—for example, lengths and pointers—are always in the native format.  
  
 *Events*  
 To receive data asynchronously, an event handle is passed in the semaphore field of the VCB. This event must be in the nonsignaled state when passed to CPI-C, and the handle must have EVENT_MODIFY_STATE access to the event.  
  
 *Library name*  
 The Win32® DLL name is WINCPIC32.DLL.  
  
 *Multiple threads*  
 A transaction program (TP) can have multiple threads that issue verbs. Windows CPI-C makes provisions for multithreaded Windows-based processes. A process contains one or more threads of execution. All references to threads refer to actual threads in a multithreaded Windows environment.  
  
 *Packing*  
 For performance reasons, the VCBs are not packed. As a result, DWORDs are on DWORD boundaries, WORDs on WORDs, and BYTEs on BYTEs. VCBs should be accessed using the structures provided.  
  
 *Run-time linking*  
 For a TP to be dynamically linked to CPI-C at run time, the TP must issue:  
  
- **LoadLibrary** to dynamically load WINCPIC.DLL or WINCPIC32.DLL, the libraries for WINCPIC.  
  
- **GetProcAddress** to specify WINCPIC as the desired entry point to the dynamic-link library (DLL).  
  
- **FreeLibrary** when the CPI-C library is no longer required.  
  
  *Simultaneous conversations*  
  A program can simultaneously participate in as many as 64 conversations per process.  
  
  *Terminating applications*  
  In Windows operating systems, CPI-C cannot tell when an application terminates. Therefore, if an application must close (for example, it receives a WM_CLOSE message as a result of an ALT+F4 from a user), the application should call [WinCPICCleanup](./wincpiccleanup2.md).  
  
  *Yielding to other components*  
  When processing CPI-C and Common Service Verbs (CSV), it may be necessary for the library code to yield to enable another component, such as the SnaBase, to receive messages and pass them to the application. This can be accomplished by using the Windows extensions [WinCPICSetBlockingHook](./wincpicsetblockinghook2.md) and [WinCPICUnhookBlockingHook](./wincpicunhookblockinghook2.md).  
  
  **WinCPICSetBlockingHook** enables a Windows CPI-C implementation to block CPI-C function calls by means of a new function. To call **WinCPICSetBlockingHook**:  
  
```  
FARPROC WINAPI WinCPICSetBlockingHook (FARPROC 1pBlockFunc)  
```  
  
 **WinCPICUnhookBlockingHook** removes any previous blocking hook that has been installed and reinstalls the default blocking mechanism. To call **WinCPICUnhookBlockingHook**:  
  
```  
BOOL WINAPI WinCPICUnhookBlockingHook (void)  
```