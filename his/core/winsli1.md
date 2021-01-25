---
description: "Learn more about: WinSLI"
title: "WinSLI1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3df18dc-b603-4150-b99a-e821f495f20d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# WinSLI
The **WinSLI** function provides asynchronous message notification for all Microsoft® Windows®-based Session Level Interface (SLI) verbs.  
  
## Syntax  
  
```  
  
          int WINAPI WinSLI(   
HWND hWnd,                    
  LUA_VERB_RECORD FAR *lpVCB  );  
```  
  
#### Parameters  
 *hWnd*  
 Handle of window to receive message.  
  
 *lpVCB*  
 Pointer to the logical unit application (LUA) verb control block (VCB), **LUA_VERB_RECORD**.  
  
## Return Value  
 The function returns a value indicating whether the request was accepted by the Windows-based SLI for processing. A returned value of zero indicates that the request was accepted and will be processed. A value other than zero indicates an error. Possible error codes are as follows:  
  
 WLUAINVALIDHANDLE  
 The window handle provided is invalid.  
  
 WLUASTARTUPNOTCALLED  
 The application has not initiated a session using [WinSLIStartup](../core/winslistartup2.md).  
  
 The value returned in **lua_flag2.async** indicates whether asynchronous notification will occur. If the flag is set (nonzero), asynchronous notification will occur through a message posted to the applications message queue. If the flag is not set, the request completed synchronously. Examine the primary return code and secondary return code for any error conditions.  
  
## Remarks  
 When the asynchronous operation is complete, the applications window *hWnd* receives the message returned by **RegisterWindowMessage** with "WinSLI" as the input string. The *lParam* argument contains the address of the VCB being posted as complete. The *wParam* argument is undefined.  
  
> [!NOTE]
>  It is possible for the request to be accepted for processing (the function call returns zero) but rejected later with a primary return code and secondary return code set in the VCB. Examine the primary return code and secondary return code for any error conditions.  
  
 If the application calls **WinSLI** without first initializing the session using **WinSLIStartup**, an error is returned.  
  
## See Also  
 [SLI](../core/sli2.md)   
 [WinSLIStartup](../core/winslistartup2.md)
