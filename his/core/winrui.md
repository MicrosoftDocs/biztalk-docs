---
title: "WinRUI1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf1c85f1-da11-41ed-a11d-e7ff61708004
caps.latest.revision: 3
---
# WinRUI
The **WinRUI** function provides asynchronous message notification for all Microsoft® Windows®-based Request Unit Interface (RUI) verbs.  
  
## Syntax  
  
```  
  
int WINAPI WinRUI(   
HWND hWnd,    
LUA_VERB_RECORD FAR *lpVCB  
);  
```  
  
#### Parameters  
 *hWnd*  
 Handle of window to receive message.  
  
 *lpVCB*  
 Pointer to the logical unit application (LUA) verb control block (VCB), **LUA_VERB_RECORD**.  
  
## Return Value  
 The function returns a value indicating whether the request was accepted by the Windows-based RUI for processing. A returned value of zero indicates that the request was accepted and will be processed. A value other than zero indicates an error. Possible error codes are as follows:  
  
 WLUAINVALIDHANDLE  
 The window handle provided is invalid.  
  
 WLUASTARTUPNOTCALLED  
 The application has not initiated a session using [WinRUIStartup](../core/winruistartup.md).  
  
 The value returned in **lua_flag2.async** indicates whether asynchronous notification will occur. If the flag is set (nonzero), asynchronous notification will occur through a message posted to the applications message queue. If the flag is not set, the request completed synchronously. Examine the primary return code and secondary return code for any error conditions.  
  
## Remarks  
 When the asynchronous operation is complete, the applications window *hWnd* receives the message returned by **RegisterWindowMessage** with "WinRUI" as the input string. The *lParam* argument contains the address of the VCB being posted as complete. The *wParam* argument is undefined.  
  
> [!NOTE]
>  It is possible for the request to be accepted for processing (the function call returns zero) but rejected later with a primary return code and secondary return code set in the VCB. Examine the primary return code and secondary return code for any error conditions.  
  
 If the application calls **WinRUI** without first initializing the session using **WinRUIStartup**, an error is returned.  
  
## See Also  
 [RUI](../core/rui.md)   
 [WinRUIStartup](../core/winruistartup.md)