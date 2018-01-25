---
title: "APPC Verbs and Windows Extensions1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f5bf835f-4570-484f-9f40-7d9f494d9aff
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# APPC Verbs and Windows Extensions
This topic describes the APPC verbs and Windows extensions that are supported by Host Integration Server:  
  
## APPC Verbs  
 The following APPC verb descriptions contain important features and should be read before using this version of Windows APPC.  
  
 ALLOCATE or MC_ALLOCATE  
 Issued by the invoking transaction program (TP), this verb allocates a session between the local logical unit (LU) and partner LU and (in conjunction with RECEIVE_ALLOCATE) establishes a conversation between the invoking TP and the invokable TP. After this verb executes successfully, APPC generates a conversation identifier (**conv_id**). The **conv_id** is a required parameter for all other APPC conversation verbs.  
  
 For a user or group using TPs, 5250 emulators, or APPC applications, you can assign default local and remote LUs. In this case, the field for LU alias is left blank or null and the default LUs are accessed when the user or group member starts an APPC program. For more information about using default LUs, see the Network Integration section of the Microsoft Host Integration Server Help.  
  
 RECEIVE_ALLOCATE  
 Issued by the invokable TP to confirm that it is ready to begin a conversation with the invoking TP that issued ALLOCATE or MC_ALLOCATE. This must be the first APPC verb issued by the invokable TP. The initial state is RESET. If the verb executes successfully (**primary_rc** is AP_OK), the state changes to RECEIVE.  
  
 RECEIVE_AND_POST or MC_RECEIVE_AND_POST  
 Receives application data and status information asynchronously. This enables the local TP to proceed with processing while data is still arriving at the local LU. RECEIVE_AND_POST and MC_RECEIVE_AND_POST are only supported by the Windows operating system.  
  
 While an asynchronous RECEIVE_AND_POST or MC_RECEIVE_AND_POST is outstanding, the following verbs can be issued:  
  
 REQUEST_TO_SEND or MC_REQUEST_TO_SEND  
  
 GET_TYPE  
  
 GET_ATTRIBUTES or MC_GET_ATTRIBUTES  
  
 TEST_RTS or MC_TEST_RTS  
  
 DEALLOCATE  
  
 SEND_ERROR or MC_SEND_ERROR  
  
 TP_ENDED  
  
 RECEIVE_AND_WAIT or MC_RECEIVE_AND_WAIT  
 Receives any data that is currently available from the partner TP. If no data is currently available, the local TP waits for data to arrive.  
  
 RECEIVE_AND_WAIT and MC_RECEIVE_AND_WAIT have been altered to act like RECEIVE_AND_POST and MC_RECEIVE_AND_POST. While an asynchronous RECEIVE_AND_WAIT or MC_RECEIVE_AND_WAIT is outstanding, the following verbs can be issued:  
  
 REQUEST_TO_SEND or MC_REQUEST_TO_SEND  
  
 GET_TYPE  
  
 GET_ATTRIBUTES or MC_GET_ATTRIBUTES  
  
 TEST_RTS or MC_TEST_RTS  
  
 DEALLOCATE  
  
 SEND_ERROR or MC_SEND_ERROR  
  
 TP_ENDED  
  
 TP_STARTED  
 Issued by the invoking TP, this verb notifies APPC that the TP is starting. For a user or group using TPs, 5250 emulators, or APPC applications, you can assign default local and remote APPC LUs. These default LUs are accessed when the user or group member starts an APPC program (a TP, 5250 emulator, or APPC application) and the program does not specify LU aliases. For more information about using default LUs, see Network Integration Help.  
  
## Limits  
 Host Integration Server permits one outstanding Windows APPC asynchronous call per connection and one blocking verb per thread. For example:  
  
```  
void ProcessVerbCompletion (WPARAM wParam, LPARAM lParam)  
{     
    int i;  
    for (i = 0; i < nPendingVerbs; i++)  
        if (pPendingVerbs[i].hAsync == wParam)  
            ProcessVCB( (LPVCB) lParam);  
}    . . .  
LRESULT CALLBACK SampleWndProc ( ... )  
{  
    if (msg == uAsyncAPPC) {  
        ProcessVerbCompletion(wParam; lParam);  
    }  
        else switch (msg) {  
        case WM_USER:  
            if (hAsync = WinAsyncAPPC(hwnd, &vcb))  
               pPendingVerbs [nPendingVerbs++].hAsync = hAsync;  
            break;  
    }  
}  
WinMain ( ... )  
{  
    if ( ( WinAPPCStartup ( ...) = = FALSE ) {  
    return FALSE ;  
    }  
    uAsyncAPPC = RegisterWindowsMessage ("WinAsyncAPPC") ;  
    while (GetMessage ( ...)  )  {  
    ...  
    WinAPPCCleanup ( ... )  
}  
```  
  
> [!NOTE]
>  The exceptions to the rule of one outstanding asynchronous call are RECEIVE_AND_POST, MC_RECEIVE_AND_POST, RECEIVE_AND_WAIT, and MC_RECEIVE_AND_WAIT. While these verbs are outstanding, certain other verbs can also be called.