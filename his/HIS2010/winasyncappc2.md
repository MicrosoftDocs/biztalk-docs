---
title: "WinAsyncAPPC2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8d80541-f87b-48fe-8439-4a26cf10b2f9
caps.latest.revision: 3
---
# WinAsyncAPPC
The **WinAsyncAPPC** function provides an asynchronous entry point for all of the APPC verbs. Use this function instead of the blocking versions of the verbs if you run your application and want to use message posting using Windows handles for asynchronous verb completion.  
  
## Syntax  
  
```  
  
HANDLE WINAPI WinAsyncAPPC(   
HANDLE hWnd,  
Long lpVcb  
);  
```  
  
#### Parameters  
 *hWnd*  
 A window handle that will be used for message posting to notify an application when an APPC verb completes.  
  
 *lpVcb*  
 Pointer to the verb control block.  
  
## Return Value  
 The return value specifies whether the asynchronous request was successful. If the function was successful, the return value is an asynchronous task handle. If the function was not successful, a zero is returned.  
  
 When this function returns with a successful value, this does not indicate that the APPC call will ultimately return successfully. It only indicates that it was possible for the APPC library to attempt the APPC call asynchronously using message posting for notification.  
  
## Remarks  
 For an example of how to use this verb in transaction programs (TPs), see the send and receive sample TP (SENDRECV.C located in the APPC folder) included in the SDK.  
  
 APPC verbs used in basic conversations that can block are as follows:  
  
-   [ALLOCATE](../HIS2010/allocate1.md)  
  
-   [CONFIRM](../HIS2010/confirm1.md)  
  
-   [CONFIRMED](../HIS2010/confirmed2.md)  
  
-   [DEALLOCATE](../HIS2010/deallocate1.md)  
  
-   [FLUSH](../HIS2010/flush1.md)  
  
-   [PREPARE_TO_RECEIVE](../HIS2010/prepare-to-receive1.md)  
  
-   [RECEIVE_ALLOCATE](../HIS2010/receive-allocate2.md)  
  
-   [RECEIVE_AND_WAIT](../HIS2010/receive-and-wait1.md)  
  
-   [REQUEST_TO_SEND](../HIS2010/request-to-send2.md)  
  
-   [SEND_CONVERSATION](../HIS2010/send-conversation1.md)  
  
-   [SEND_DATA](../HIS2010/send-data2.md)  
  
-   [SEND_ERROR](../HIS2010/send-error1.md)  
  
-   [TP_ENDED](../HIS2010/tp-ended2.md)  
  
-   [TP_STARTED](../HIS2010/tp-started1.md)  
  
 APPC verbs used in mapped conversations that can block are as follows:  
  
-   [MC_ALLOCATE](../HIS2010/mc-allocate1.md)  
  
-   [MC_CONFIRM](../HIS2010/mc-confirm1.md)  
  
-   [MC_CONFIRMED](../HIS2010/mc-confirmed2.md)  
  
-   [MC_DEALLOCATE](../HIS2010/mc-deallocate1.md)  
  
-   [MC_FLUSH](../HIS2010/mc-flush2.md)  
  
-   [MC_PREPARE_TO_RECEIVE](../HIS2010/mc-prepare-to-receive2.md)  
  
-   [MC_RECEIVE_AND_WAIT](../HIS2010/mc-receive-and-wait1.md)  
  
-   [MC_REQUEST_TO_SEND](../HIS2010/mc-request-to-send2.md)  
  
-   [MC_SEND_CONVERSATION](../HIS2010/mc-send-conversation2.md)  
  
-   [MC_SEND_DATA](../HIS2010/mc-send-data2.md)  
  
-   [MC_SEND_ERROR](../HIS2010/mc-send-error1.md)  
  
 When using the synchronous or asynchronous versions of a verb, an application can only have one outstanding function in progress on a conversation at a time. An attempt to initiate a second function results in the error code AP_CONV_BUSY.  
  
 The exceptions to the preceding paragraph are:  
  
-   [RECEIVE_AND_POST](../HIS2010/receive-and-post2.md)  
  
-   [MC_RECEIVE_AND_POST](../HIS2010/mc-receive-and-post1.md)  
  
-   [RECEIVE_AND_WAIT](../HIS2010/receive-and-wait1.md)  
  
-   [MC_RECEIVE_AND_WAIT](../HIS2010/mc-receive-and-wait1.md)  
  
 To allow full use of the asynchronous support, asynchronously issued **RECEIVE_AND_WAIT** and **MC_RECEIVE_AND_WAIT** verbs have been altered to act like the **RECEIVE_AND_POST** and **MC_RECEIVE_AND_POST** verbs. Specifically, while an asynchronous version of one of these verbs is outstanding, the following verbs can be issued on the same conversation:  
  
-   [DEALLOCATE](../HIS2010/deallocate1.md) (AP_ABEND_PROG, AP_ABEND_SVC, or AP_ABEND_TIMER)  
  
-   [GET_ATTRIBUTES](../HIS2010/get-attributes1.md) or [MC_GET_ATTRIBUTES](../HIS2010/mc-get-attributes1.md)  
  
-   [GET_TYPE](../HIS2010/get-type1.md)  
  
-   [REQUEST_TO_SEND](../HIS2010/request-to-send2.md) or [MC_REQUEST_TO_SEND](../HIS2010/mc-request-to-send2.md)  
  
-   [SEND_ERROR](../HIS2010/send-error1.md) or [MC_SEND_ERROR](../HIS2010/mc-send-error1.md)  
  
-   [TEST_RTS](../HIS2010/test-rts1.md) or [MC_TEST_RTS](../HIS2010/mc-test-rts1.md)  
  
-   [TP_ENDED](../HIS2010/tp-ended2.md)  
  
 This allows an application, in particular, a 5250 emulator, to use an asynchronous **RECEIVE_AND_WAIT** or **MC_RECEIVE_AND_WAIT** to receive data. While the **RECEIVE_AND_POST**, **MC_RECEIVE_AND_POST**, **RECEIVE_AND_WAIT**, or **MC_RECEIVE_AND_WAIT** is outstanding, it can still use **SEND_ERROR** or **MC_SEND_ERROR** and **REQUEST_TO_SEND** or **MC_REQUEST_TO_SEND**. It is recommended that you use this feature for full asynchronous support.  
  
 When the asynchronous operation is complete, the application's window *hWnd* receives the message returned by **RegisterWindowMessage** with "WinAsyncAPPC" as the input string. The *wParam* argument contains the asynchronous task handle returned by the original function call. The *lParam* argument contains the original VCB pointer and can be dereferenced to determine the final return code.  
  
 As part of the Windows APPC definition, [WinAPPCCancelAsyncRequest](../HIS2010/winappccancelasyncrequest1.md) allows an application to cancel any asynchronous APPC action; but terminates the related conversation or TP as appropriate. Any outstanding operations return with AP_CANCELED as the return code.  
  
 If the function returns successfully, a **WinAsyncAPPC** message is posted to the application when the operation completes or the conversation is canceled.