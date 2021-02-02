---
description: "Learn more about: WinCPICSetBlockingHook"
title: "WinCPICSetBlockingHook2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7fe5561a-cfa7-463a-8e48-6e78a10278d0
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# WinCPICSetBlockingHook
The **WinCPICSetBlockingHook** function allows a Microsoft® Windows® Common Programming Interface for Communications (CPI-C) implementation to block CPI-C function calls by means of a new function. This legacy call was used by Microsoft® Windows® version 3.*x* applications to make blocking calls without blocking the rest of the system. By default in the Microsoft Windows operating system, blocking calls suspend the calling applications thread until the request is finished.  
  
## Parameters  
 *lpBlockFunc*  
 Specifies the procedure instance address of the blocking function to be installed.  
  
## Return Values  
 The return value points to the procedure instance of the previously installed blocking function. The application or library that calls **WinCPICSetBlockingHook** should save this return value so that it can be restored if needed. (If nesting is not important, the application can simply discard the value returned by **WinCPICSetBlockingHook** and eventually use [WinCPICUnhookBlockingHook](../core/wincpicunhookblockinghook2.md) to restore the default mechanism.)  
  
## Remarks  
 A Windows CPI-C implementation has a default mechanism by which blocking CPI-C functions are implemented. This function gives the application the ability to execute its own function at blocking time in place of the default function.  
  
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
  
 The **WinCPICSetBlockingHook** function is provided to support applications that require more complex message processing, for example, those employing the multiple document interface (MDI) model or applications with Menu accelerators (TranslateAccelerator).  
  
 Blocking functions must return FALSE in response to a WM_QUIT message so Windows CPI-C can return control to the application to process the message and terminate gracefully. Otherwise, the function should return TRUE.  
  
## See Also  
 [Set_Processing_Mode (CPI-C)](../core/set-processing-mode-cpi-c-2.md)   
 [Specify_Windows_Handle (CPI-C)](../core/specify-windows-handle-cpi-c-2.md)
