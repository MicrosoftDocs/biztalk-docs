---
title: "WinAsyncAPPCEx2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 22b0f49b-8ab6-4c9f-81dc-3d643526ac2a
caps.latest.revision: 4
---
# WinAsyncAPPCEx
The **WinAsyncAPPCEx** function provides an asynchronous entry point for all of the APPC verbs. Use this function instead of the blocking versions of the verbs to allow multiple sessions to be handled on the same thread using events. This verb is only supported on Microsoft Windows and uses Win32® events.  
  
## Syntax  
  
```  
  
    HANDLE WINAPI WinAsyncAPPCEx(   
HANDLEevent_handle,  
longlpVcb);  
```  
  
#### Parameters  
 *event_handle*  
 Handle used for event notification using Win32 events.  
  
 *lpVcb*  
 Pointer to the verb control block.  
  
## Return Value  
 The return value specifies whether the asynchronous resolution request was successful. If the function was successful, the return value is an asynchronous task handle. If the function was not successful, a zero is returned.  
  
 When this function returns with a successful value, this does not indicate that the APPC call will ultimately return successfully. It only indicates that it was possible for the APPC library to attempt the APPC call asynchronously using events for notification.  
  
## Remarks  
 This function is intended for use with **WaitForSingleObject** or **WaitForMultipleObjects** in the Win32 API. These functions are described in the "Reference" section of the Microsoft Platform SDK documentation.  
  
 For an example of how to use this verb in multithreaded TPs, see the multithreaded send and receive sample TPs (MRCV.C, MSEND.C, and MSENDRCV.C located in the MSENDRCV folder) included in the SDK.  
  
 APPC verbs used in basic conversations that can block are as follows:  
  
-   [ALLOCATE](../core/allocate1.md)  
  
-   [CONFIRM](../core/confirm1.md)  
  
-   [CONFIRMED](../core/confirmed2.md)  
  
-   [DEALLOCATE](../core/deallocate1.md)  
  
-   [FLUSH](../core/flush1.md)  
  
-   [PREPARE_TO_RECEIVE](../core/prepare-to-receive1.md)  
  
-   [RECEIVE_ALLOCATE](../core/receive-allocate2.md)  
  
-   [RECEIVE_AND_WAIT](../core/receive-and-wait1.md)  
  
-   [REQUEST_TO_SEND](../core/request-to-send2.md)  
  
-   [SEND_CONVERSATION](../core/send-conversation1.md)  
  
-   [SEND_DATA](../core/send-data2.md)  
  
-   [SEND_ERROR](../core/send-error1.md)  
  
-   [TP_ENDED](../core/tp-ended2.md)  
  
-   [TP_STARTED](../core/tp-started1.md)  
  
 APPC verbs used in mapped conversations that can block are as follows:  
  
-   [MC_ALLOCATE](../core/mc-allocate1.md)  
  
-   [MC_CONFIRM](../core/mc-confirm1.md)  
  
-   [MC_CONFIRMED](../core/mc-confirmed2.md)  
  
-   [MC_DEALLOCATE](../core/mc-deallocate1.md)  
  
-   [MC_FLUSH](../core/mc-flush2.md)  
  
-   [MC_PREPARE_TO_RECEIVE](../core/mc-prepare-to-receive2.md)  
  
-   [MC_RECEIVE_AND_WAIT](../core/mc-receive-and-wait1.md)  
  
-   [MC_REQUEST_TO_SEND](../core/mc-request-to-send2.md)  
  
-   [MC_SEND_CONVERSATION](../core/mc-send-conversation2.md)  
  
-   [MC_SEND_DATA](../core/mc-send-data2.md)  
  
-   [MC_SEND_ERROR](../core/mc-send-error1.md)  
  
-   [RECEIVE_ALLOCATE](../core/receive-allocate2.md)  
  
-   [TP_ENDED](../core/tp-ended2.md)  
  
-   [TP_STARTED](../core/tp-started1.md)  
  
 When using the synchronous or asynchronous versions of a verb, an application can only have one outstanding function in progress on a conversation at a time. An attempt to initiate a second function results in the error code AP_CONV_BUSY.  
  
> [!NOTE]
>  The exceptions to the preceding paragraph are [RECEIVE_AND_POST](../core/receive-and-post2.md), [MC_RECEIVE_AND_POST](../core/mc-receive-and-post1.md), [RECEIVE_AND_WAIT](../core/receive-and-wait1.md), and [MC_RECEIVE_AND_WAIT](../core/mc-receive-and-wait1.md).  
  
> [!NOTE]
>  To allow full use of the asynchronous support, asynchronously issued **RECEIVE_AND_WAIT** and **MC_RECEIVE_AND_WAIT** verbs have been altered to act like the **RECEIVE_AND_POST** and **MC_RECEIVE_AND_POST** verbs. Specifically, while an asynchronous version of one of these verbs is outstanding, the following verbs can be issued on the same conversation:  
  
-   [DEALLOCATE](../core/deallocate1.md) (AP_ABEND_PROG, AP_ABEND_SVC, or AP_ABEND_TIMER)  
  
-   [GET_ATTRIBUTES](../core/get-attributes1.md) or [MC_GET_ATTRIBUTES](../core/mc-get-attributes1.md)  
  
-   [GET_TYPE](../core/get-type1.md)  
  
-   [REQUEST_TO_SEND](../core/request-to-send2.md) or [MC_REQUEST_TO_SEND](../core/mc-request-to-send2.md)  
  
-   [SEND_ERROR](../core/send-error1.md) or [MC_SEND_ERROR](../core/mc-send-error1.md)  
  
-   [TEST_RTS](../core/test-rts1.md) or [MC_TEST_RTS](../core/mc-test-rts1.md)  
  
-   [TP_ENDED](../core/tp-ended2.md)  
  
> [!NOTE]
>  This allows an application, in particular, a server application, to use an asynchronous **RECEIVE_AND_WAIT** or **MC_RECEIVE_AND_WAIT** to receive data. While the **RECEIVE_AND_POST**, **MC_RECEIVE_AND_POST**, **RECEIVE_AND_WAIT**, or **MC_RECEIVE_AND_WAIT** is outstanding, it can still use **SEND_ERROR** or **MC_SEND_ERROR** and **REQUEST_TO_SEND** or **MC_REQUEST_TO_SEND**. It is recommended that you use this feature for full asynchronous support, and in particular, for support of multiple conversations on the same thread.  
  
 When the asynchronous operation is complete, the application is notified through the signaling of the event. Upon signaling of the event, examine the APPC primary return code and secondary return code in the verb control block for any error conditions.