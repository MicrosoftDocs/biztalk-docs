---
title: "WinAsyncAPPC1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ceb62f30-4b7b-471f-87c3-76b4e1a2dbde
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
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
  
- [ALLOCATE](../core/allocate2.md)  
  
- [CONFIRM](../core/confirm2.md)  
  
- [CONFIRMED](../core/confirmed1.md)  
  
- [DEALLOCATE](../core/deallocate2.md)  
  
- [FLUSH](../core/flush2.md)  
  
- [PREPARE_TO_RECEIVE](../core/prepare-to-receive2.md)  
  
- [RECEIVE_ALLOCATE](../core/receive-allocate1.md)  
  
- [RECEIVE_AND_WAIT](../core/receive-and-wait2.md)  
  
- [REQUEST_TO_SEND](../core/request-to-send1.md)  
  
- [SEND_CONVERSATION](../core/send-conversation2.md)  
  
- [SEND_DATA](../core/send-data1.md)  
  
- [SEND_ERROR](../core/send-error2.md)  
  
- [TP_ENDED](../core/tp-ended1.md)  
  
- [TP_STARTED](../core/tp-started2.md)  
  
  APPC verbs used in mapped conversations that can block are as follows:  
  
- [MC_ALLOCATE](../core/mc-allocate2.md)  
  
- [MC_CONFIRM](../core/mc-confirm2.md)  
  
- [MC_CONFIRMED](../core/mc-confirmed1.md)  
  
- [MC_DEALLOCATE](../core/mc-deallocate2.md)  
  
- [MC_FLUSH](../core/mc-flush1.md)  
  
- [MC_PREPARE_TO_RECEIVE](../core/mc-prepare-to-receive1.md)  
  
- [MC_RECEIVE_AND_WAIT](../core/mc-receive-and-wait2.md)  
  
- [MC_REQUEST_TO_SEND](../core/mc-request-to-send1.md)  
  
- [MC_SEND_CONVERSATION](../core/mc-send-conversation1.md)  
  
- [MC_SEND_DATA](../core/mc-send-data1.md)  
  
- [MC_SEND_ERROR](../core/mc-send-error2.md)  
  
  When using the synchronous or asynchronous versions of a verb, an application can only have one outstanding function in progress on a conversation at a time. An attempt to initiate a second function results in the error code AP_CONV_BUSY.  
  
  The exceptions to the preceding paragraph are:  
  
- [RECEIVE_AND_POST](../core/receive-and-post1.md)  
  
- [MC_RECEIVE_AND_POST](../core/mc-receive-and-post2.md)  
  
- [RECEIVE_AND_WAIT](../core/receive-and-wait2.md)  
  
- [MC_RECEIVE_AND_WAIT](../core/mc-receive-and-wait2.md)  
  
  To allow full use of the asynchronous support, asynchronously issued **RECEIVE_AND_WAIT** and **MC_RECEIVE_AND_WAIT** verbs have been altered to act like the **RECEIVE_AND_POST** and **MC_RECEIVE_AND_POST** verbs. Specifically, while an asynchronous version of one of these verbs is outstanding, the following verbs can be issued on the same conversation:  
  
- [DEALLOCATE](../core/deallocate2.md) (AP_ABEND_PROG, AP_ABEND_SVC, or AP_ABEND_TIMER)  
  
- [GET_ATTRIBUTES](../core/get-attributes2.md) or [MC_GET_ATTRIBUTES](../core/mc-get-attributes2.md)  
  
- [GET_TYPE](../core/get-type2.md)  
  
- [REQUEST_TO_SEND](../core/request-to-send1.md) or [MC_REQUEST_TO_SEND](../core/mc-request-to-send1.md)  
  
- [SEND_ERROR](../core/send-error2.md) or [MC_SEND_ERROR](../core/mc-send-error2.md)  
  
- [TEST_RTS](../core/test-rts2.md) or [MC_TEST_RTS](../core/mc-test-rts2.md)  
  
- [TP_ENDED](../core/tp-ended1.md)  
  
  This allows an application, in particular, a 5250 emulator, to use an asynchronous **RECEIVE_AND_WAIT** or **MC_RECEIVE_AND_WAIT** to receive data. While the **RECEIVE_AND_POST**, **MC_RECEIVE_AND_POST**, **RECEIVE_AND_WAIT**, or **MC_RECEIVE_AND_WAIT** is outstanding, it can still use **SEND_ERROR** or **MC_SEND_ERROR** and **REQUEST_TO_SEND** or **MC_REQUEST_TO_SEND**. It is recommended that you use this feature for full asynchronous support.  
  
  When the asynchronous operation is complete, the application's window *hWnd* receives the message returned by **RegisterWindowMessage** with "WinAsyncAPPC" as the input string. The *wParam* argument contains the asynchronous task handle returned by the original function call. The *lParam* argument contains the original VCB pointer and can be dereferenced to determine the final return code.  
  
  As part of the Windows APPC definition, [WinAPPCCancelAsyncRequest](../core/winappccancelasyncrequest2.md) allows an application to cancel any asynchronous APPC action; but terminates the related conversation or TP as appropriate. Any outstanding operations return with AP_CANCELED as the return code.  
  
  If the function returns successfully, a **WinAsyncAPPC** message is posted to the application when the operation completes or the conversation is canceled.