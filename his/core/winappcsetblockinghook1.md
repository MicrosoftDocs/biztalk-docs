---
title: "WinAPPCSetBlockingHook1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb9660dc-1138-4aea-a7f2-487211e338a8
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WinAPPCSetBlockingHook
The **WinAPPCSetBlockingHook** function allows a Windows APPC implementation to block APPC function calls by means of a new function. By default in Microsoft Windows, blocking calls suspend the calling application's thread until the request is finished.  
  
## Syntax  
  
```  
  
    FARPROC WINAPI WinAPPCSetBlockingHook (   
FARPROC lpBlockFunc);  
```  
  
#### Parameters  
 *lpBlockFunc*  
 Specifies the procedure instance address of the blocking function to be installed.  
  
## Return Value  
 The return value points to the procedure instance of the previously installed blocking function. The application or library that calls **WinAPPCSetBlockingHook** should save this return value so that it can be restored if needed. (If nesting is not important, the application can simply discard the value returned by **WinAPPCSetBlockingHook** and eventually use [WinAPPCUnhookBlockingHook](../core/winappcunhookblockinghook2.md) to restore the default mechanism.)  
  
## Remarks  
 A Windows APPC implementation has a default mechanism by which blocking APPC functions are implemented. This function gives the application the ability to execute its own function at blocking time in place of the default function.  
  
 The default blocking function is equivalent to:  
  
```  
BOOL DefaultBlockingHook (void)  {  
    MSG msg;  
    /* get the next message if any */  
    if ( PeekMessage (&msg,0,0,PM_NOREMOVE)  )  {  
        if ( msg.message = = WM_QUIT  )  
            return FALSE;   // let app process WM_QUIT  
        PeekMessage (&msg,0,0,PM_REMOVE) ;  
        TranslateMessage (&msg) ;  
        DispatchMessage (&msg) ;  
    }  
    /* TRUE if no WM_QUIT received */  
    return TRUE;  
}  
```  
  
 A blocking function must return FALSE if it receives a WM_QUIT message so Windows APPC can return control to the application to process the message and terminate gracefully. Otherwise, the function should return TRUE.  
  
 This function is implemented on a per-thread basis. It provides for a particular thread to replace the blocking mechanism without affecting other threads.  
  
 The **WinAPPCSetBlockingHook** function is provided to support those applications that require more complex message processing—for example, those employing the multiple document interface (MDI) model.  
  
## See Also  
 [WinAPPCIsBlocking](../core/winappcisblocking1.md)   
 [WinAPPCCancelBlockingCall](../core/winappccancelblockingcall1.md)