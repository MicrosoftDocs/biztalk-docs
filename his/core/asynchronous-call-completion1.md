---
title: "Asynchronous Call Completion1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8112926f-73fa-45b5-9972-020161401ada
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Asynchronous Call Completion
With one exception, Microsoft® Host Integration Server permits one outstanding Windows® SNA asynchronous call per connection and one blocking verb per thread. The exception to this is that when issuing an asynchronous [Receive](../HIS2010/receive-cpi-c-1.md) call, the following calls can be issued while the **Receive** is outstanding:  
  
-   [Cancel_Conversation](../HIS2010/cancel-conversation-cpi-c-1.md)  
  
-   [Deallocate](../HIS2010/deallocate-cpi-c-2.md)  
  
-   [Request_To_Send](../HIS2010/request-to-send-cpi-c-2.md)  
  
-   [Send_Error](../HIS2010/send-error-cpi-c-1.md)  
  
-   [Test_Request_To_Send_Received](../HIS2010/test-request-to-send-received-cpi-c-2.md)  
  
 This enables an application, in particular a 5250 emulator, to use an asynchronous **Receive** to receive data. Use of this feature is strongly recommended.  
  
 The following example illustrates how to use asynchronous call completion with Host Integration Server:  
  
```  
void ProcessVerbCompletion (WPARAM wParam LPARAM lParam)  
{  
    for ( i = 0; i<nPendingVerbs; i++ )  
        if (memcmp  (pPending [i].ConvID, (Conversation_ID) lParam)== 0)  
            ProcessCommand  (wParam, lParam);  
}  
  
LRESULT CALLBACK SampleWndProc  ( . . .)  
{  
    if (msg = = uAsyncCPIC ) {  
        ProcessVerbCompletion (wParam, lParam);  
    }  
    else switch  (msg)  {  
       case WM_USER:  
        Initialize_Conversation (lpConvId, "GORDM", &lError  );  
        if  (lError  ! = CM_OK )   {  
            ErrorDisplay ( ) ;  
            break ;  
        }  
        Set_Processing_Mode (lpConvId, CM_NON_BLOCKING, &lError  ) ;  
        if  ( lError ! = CM_OK )  {  
            ErrorDisplay ( ) ;  
            break ;  
        }  
        Allocate  (lpConvId,  &lError )  ;  
        switch  (lError )  {  
        case CM_OK:  
            break ;  
        case CM_OPERATION_INCOMPLETE:  
            memcopy (pPending [nPending ++].ConvId, lpConvId, sizeof (C) ;  
            break ;  
        default:  
            ErrorDisplay ( ) ;  
        }  
        break ;  
}  
WinMain  ( . . . )  
{  
    if  ( ( WinCPICStartup  ( . . . )  =  =  FALSE  )   {  
        return FALSE;  
    }  
    uAsyncCPIC = RegisterWindowMessage  ("WinAsyncCPIC"");  
    Specify_Windows_Handle  (hwndSample) ;  
    while  (GetMessage  ( . . . )   )   {  
    . . . . .  
    }  
    WinCPICCleanup  ( . . . )  
}  
```  
  
 For more information about CPI-C calls and Windows extensions, see [CPI-C Calls](../HIS2010/cpi-c-calls1.md) and [Extensions for the Windows Environment](../HIS2010/extensions-for-the-windows-environment2.md). For additional information about using CPI-C, see the *IBM Systems Application Architecture Common Programming Interface Communications Reference*, part number SC26-4399-04.