---
title: "WinAsyncAPPCIOCP1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c358c5b0-f8e9-4306-aa32-0905708cc177
caps.latest.revision: 4
---
# WinAsyncAPPCIOCP
The **WinAsyncAPPCIOCP** function provides an asynchronous entry point for all of the APPC verbs. Use this function instead of the blocking versions of the verbs to allow multiple sessions to be handled on the same thread using I/O completion ports. This verb is only supported on Microsoft Windows, and uses Win32 I/O completion ports.  
  
## Syntax  
  
```  
  
    HANDLE WINAPI WinAsyncAPPCIOCP(   
APPC_IOCP_INFO *iocp_handle,  
longlpVcb);  
```  
  
#### Parameters  
 *iocp_handle*  
 A pointer to an **APPC_IOCP_INFO** structure used for passing I/O completion port information.  
  
 *lpVcb*  
 Pointer to the verb control block  
  
 The **APPC_IOCP_INFO** structure has the following prototype:  
  
```  
  
APPC_CompletionPort;APPC_NumberOfBytesTransferred;  
    APPC_CompletionKey;  
    APPC_pOverlapped;  
  
```  
  
 *APPC_CompletionPort*  
  
 This supplied parameter is the HANDLE returned by the call to the **CreateIoCompletionPort** function when the I/O completion port is created. The I/O completion port must be created before calling the **WinAsyncAPPCIOCP** function. When the verb completes, the APPC Library calls the **PostQueuedCompletionStatus** function with the remaining fields in the structure as inputs, and these fields are simply passed through to the **GetQueuedCompletionStatus** function issued by the application.  
  
 *APPC_NumberOfBytesTransferred*  
  
 This supplied parameter is ignored. When the APPC verb completes, the APPC Library calls the **PostQueuedCompletionStatus** function with this field as an input, and the value returned for the *dwNumberOfBytesTransferred* is simply passed through to the **GetQueuedCompletionStatus** function issued by the application.  
  
 *APPC_CompletionKey*  
  
 This supplied parameter is ignored. When the APPC verb completes, the APPC Library calls the **PostQueuedCompletionStatus** function with this field as an input, and the value returned for the *dwCompletionKey* is simply passed through to the **GetQueuedCompletionStatus** function issued by the application.  
  
 *APPC_pOverlapped*  
  
 This supplied parameter is ignored. When the APPC verb completes, the APPC Library calls the **PostQueuedCompletionStatus** function with this field as an input, and the value returned for the *lpOverlapped* is simply passed through to the **GetQueuedCompletionStatus** function issued by the application.  
  
## Return Value  
 The return value specifies whether the asynchronous resolution request was successful. If the function was successful, the return value is an asynchronous task handle. If the function was not successful, a zero is returned.  
  
 When this function returns with a successful value, this does not indicate that the APPC call will ultimately return successfully. It only indicates that it was possible for the APPC library to attempt the APPC call asynchronously using an I/O completion port for notification.  
  
## Remarks  
 This function is intended for use with **CreateIoCompletionPort** and **GetQueuedCompletionStatus** in the Win32 API. These functions are described in the "Reference" section of the Microsoft Platform SDK documentation.  
  
 For an example of how to use this verb in multithreaded TPs, see the multithreaded receive sample TP (MRCVIO located in the SNA\MSENDRCV folder) using I/O completion ports included in the [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] SDK.  
  
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
  
 The exceptions to the preceding paragraph are [RECEIVE_AND_POST](../core/receive-and-post2.md), [MC_RECEIVE_AND_POST](../core/mc-receive-and-post1.md), [RECEIVE_AND_WAIT](../core/receive-and-wait1.md), and [MC_RECEIVE_AND_WAIT](../core/mc-receive-and-wait1.md).  
  
 To allow full use of the asynchronous support, asynchronously issued **RECEIVE_AND_WAIT** and **MC_RECEIVE_AND_WAIT** verbs have been altered to act like the **RECEIVE_AND_POST** and **MC_RECEIVE_AND_POST** verbs. Specifically, while an asynchronous version of one of these verbs is outstanding, the following verbs can be issued on the same conversation:  
  
-   [DEALLOCATE](../core/deallocate1.md) (AP_ABEND_PROG, AP_ABEND_SVC, or AP_ABEND_TIMER)  
  
-   [GET_ATTRIBUTES](../core/get-attributes1.md) or [MC_GET_ATTRIBUTES](../core/mc-get-attributes1.md)  
  
-   [GET_TYPE](../core/get-type1.md)  
  
-   [REQUEST_TO_SEND](../core/request-to-send2.md) or [MC_REQUEST_TO_SEND](../core/mc-request-to-send2.md)  
  
-   [SEND_ERROR](../core/send-error1.md) or [MC_SEND_ERROR](../core/mc-send-error1.md)  
  
-   [TEST_RTS](../core/test-rts1.md) or [MC_TEST_RTS](../core/mc-test-rts1.md)  
  
-   [TP_ENDED](../core/tp-ended2.md)  
  
 This allows an application, in particular, a server application, to use an asynchronous **RECEIVE_AND_WAIT** or **MC_RECEIVE_AND_WAIT** to receive data. While the **RECEIVE_AND_POST**, **MC_RECEIVE_AND_POST**, **RECEIVE_AND_WAIT**, or **MC_RECEIVE_AND_WAIT** is outstanding, it can still use **SEND_ERROR** or **MC_SEND_ERROR** and **REQUEST_TO_SEND** or **MC_REQUEST_TO_SEND**. It is recommended that you use this feature for full asynchronous support, and in particular, for support of multiple conversations on the same thread.  
  
 When the asynchronous operation is complete, the application is notified through the **GetQueuedCompletionStatus** function. Upon I/O completion, examine the APPC primary return code and secondary return code in the verb control block for any error conditions.