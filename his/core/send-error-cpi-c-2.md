---
title: "Send_Error (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 07fad27b-353e-46ee-a9de-7cc43ba02386
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Send_Error (CPI-C)
The **Send_Error** call (function name **cmserr**) notifies the partner program that the local program has encountered an application-level error.  
  
## Syntax  
  
```  
  
CM_ENTRY Send_Error(   
  unsigned char FAR *conversation_ID,    
    CM_INT32 FAR *request_to_send_received,    
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 *request_to_send_received*  
 Returned parameter. Specifies the request-to-send-received indicator. Possible values are:  
  
 CM_REQ_TO_SEND_RECEIVED  
 The partner program issued [Request_To_Send](../core/request-to-send-cpi-c-1.md), which requests the local program to change the conversation to RECEIVE state.  
  
 CM_REQ_TO_SEND_NOT_RECEIVED  
 The partner program did not issue **Request_To_Send**. This value is not relevant if *return_code* is set to CM_PROGRAM_PARAMETER_CHECK or CM_STATE_CHECK.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 The value of *return_code* varies depending on the conversation state when the call is issued.  
  
 **SEND State**  
  
 If the program issues the call with the conversation in SEND state, the following return codes are possible:  
  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_OPERATION_NOT_ACCEPTED  
 Primary return code; a previous operation on this conversation is incomplete.  
  
 CM_OPERATION_INCOMPLETE  
 Primary return code; the operation has not completed (processing mode is nonblocking only) and is still in progress. The program can issue [Wait_For_Conversation](../core/wait-for-conversation-cpi-c-1.md) to await the completion of the operation, or [Cancel_Conversation](../core/cancel-conversation-cpi-c-2.md) to cancel the operation and conversation. If [Specify_Windows_Handle](../core/specify-windows-handle-cpi-c-2.md) has been called, the application should wait for notification by a Microsoft® Windows® message and not call **Wait_For_Conversation**.  
  
 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
 CM_CONVERSATION_TYPE_MISMATCH  
 Primary return code; the partner logical unit (LU) or program does not support the conversation type (basic or mapped) specified in the allocation request.  
  
 CM_PIP_NOT_SPECIFIED_CORRECTLY  
 Primary return code; the allocation request was rejected by a non-CPI-C LU 6.2 transaction program (TP). The partner program requires one or more PIP data variables, which are not supported by CPI-C.  
  
 CM_SECURITY_NOT_VALID  
 Primary return code; the user identifier or password specified in the allocation request was not accepted by the partner LU.  
  
 CM_SYNC LEVEL_NOT_SUPPORTED_PGM  
 Primary return code; the partner program does not support the synchronization level specified in the allocation request.  
  
 CM_TPN_NOT_RECOGNIZED  
 Primary return code; the partner LU does not recognize the program name specified in the allocation request.  
  
 CM_TP_NOT_AVAILABLE_NO_RETRY  
 Primary return code; the partner LU cannot start the program specified in the allocation request because of a permanent condition. The reason for the error may be logged on the remote node. Do not retry the allocation until the error has been corrected.  
  
 CM_TP_NOT_AVAILABLE_RETRY  
 Primary return code; the partner LU cannot start the program specified in the allocation request because of a temporary condition. The reason for the error may be logged on the remote node. Retry the allocation.  
  
 CM_PROGRAM_ERROR_PURGING  
 Primary return code; one of the following occurred:  
  
- While in RECEIVE or CONFIRM state, the partner program issued **Send_Error**. Data sent but not yet received is purged.  
  
- While in SEND_PENDING state with the error direction set to CM_RECEIVE_ERROR, the partner program issued **Send_Error**. Data was not purged.  
  
  CM_RESOURCE_FAILURE_NO_RETRY  
  Primary return code; one of the following occurred:  
  
- The conversation was terminated prematurely because of a permanent condition. Do not retry until the error has been corrected.  
  
- The partner program did not deallocate the conversation before terminating normally.  
  
  CM_RESOURCE_FAILURE_RETRY  
  Primary return code; the conversation was terminated prematurely because of a temporary condition, such as modem failure. Retry the conversation.  
  
  CM_DEALLOCATED_ABEND  
  Primary return code; the conversation has been deallocated for one of the following reasons:  
  
- The remote program issued [Deallocate](../core/deallocate-cpi-c-1.md) with the type parameterset to CM_DEALLOCATE_ABEND, or the remote LU has done so because of a remote program abnormal-ending condition. If the conversation for the remote program was in RECEIVE state when the call was issued, information sent by the local program and not yet received by the remote program is purged.  
  
- The remote TP terminated normally but did not deallocate the conversation before terminating. Node services at the remote LU deallocated the conversation on behalf of the remote TP.  
  
  CM_DEALLOCATED_ABEND_SVC  
  Primary return code; the conversation has been deallocated for one of the following reasons:  
  
- The partner program issued **Deallocate** with the type parameter set to ABEND_SVC.  
  
- The partner program did not deallocate the conversation before terminating.  
  
  If the conversation is in RECEIVE state for the partner program when this call is issued by the local program, data sent by the local program and not yet received by the partner program is purged.  
  
  CM_DEALLOCATED_ABEND_TIMER  
  Primary return code; the conversation has been deallocated because the partner program issued **Deallocate** with the type parameter set to ABEND_TIMER. If the conversation is in RECEIVE state for the partner program when this call is issued by the local program, data sent by the local program and not yet received by the partner program is purged.  
  
  CM_SVC_ERROR_PURGING  
  Primary return code; while in SEND state, the partner program or partner LU issued **Send_Error** with the type parameter set to SVC. Data sent to the partner program may have been purged.  
  
  **RECEIVE State**  
  
  If the call is issued in RECEIVE state, the following return codes are possible:  
  
  CM_OK  
  Primary return code; because incoming information is purged when the **Send_Error** call is issued in RECEIVE state, CM_OK is generated instead of the following:  
  
- CM_PROGRAM_ERROR_NO_TRUNC  
  
- CM_PROGRAM_ERROR_PURGING  
  
- CM_SVC_ERROR_NO_TRUNC  
  
- CM_SVC_ERROR_PURGING  
  
- CM_PROGRAM_ERROR_TRUNC  
  
- CM_SVC_ERROR_TRUNC (basic conversation only)  
  
- CM_PRODUCT_SPECIFIC_ERROR  
  
- CM_RESOURCE_FAILURE_NO_RETRY  
  
- CM_RESOURCE_FAILURE_RETRY  
  
  For an explanation of these return codes, see [CPI-C Common Return Codes](../core/cpi-c-common-return-codes2.md).  
  
  CM_DEALLOCATED_NORMAL  
  Primary return code; because incoming information is purged when **Send_Error** is issued in RECEIVE state, CM_DEALLOCATED_NORMAL is generated instead of the following:  
  
- CM_CONVERSATION_TYPE_MISMATCH  
  
- CM_PIP_NOT_SPECIFIED_CORRECTLY  
  
- CM_SECURITY_NOT_VALID  
  
- CM_SYNC_LEVEL_NOT_SUPPORTED_PGM  
  
- CM_TPN_NOT_RECOGNIZED  
  
- CM_TP_NOT_AVAILABLE_NO_RETRY  
  
- CM_TP_NOT_AVAILABLE_RETRY  
  
- CM_DEALLOCATED_ABEND  
  
- CM_DEALLOCATED_ABEND_SVC  
  
- CM_DEALLOCATED_ABEND_TIMER  
  
  **SEND_PENDING State**  
  
  If the call is issued in SEND_PENDING state, the following return codes are possible:  
  
- CM_OK (Primary return code; the call executed successfully.)  
  
- CM_PRODUCT_SPECIFIC_ERROR  
  
- CM_PROGRAM_ERROR_PURGING  
  
- CM_RESOURCE_FAILURE_NO_RETRY  
  
- CM_RESOURCE_FAILURE_RETRY  
  
- CM_DEALLOCATED_ABEND  
  
- CM_DEALLOCATED_ABEND_SVC  
  
- CM_DEALLOCATED_ABEND_TIMER  
  
- CM_SVC_ERROR_PURGING  
  
  For an explanation of these return codes, see [CPI-C Common Return Codes](../core/cpi-c-common-return-codes2.md).  
  
  **CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE State**  
  
  If the call is issued in CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state, the following return codes are possible:  
  
- CM_OK (Primary return code; the call executed successfully.)  
  
- CM_PRODUCT_SPECIFIC_ERROR  
  
- CM_RESOURCE_FAILURE_NO_RETRY  
  
- CM_RESOURCE_FAILURE_RETRY  
  
  For an explanation of these return codes, see [CPI-C Common Return Codes](../core/cpi-c-common-return-codes2.md).  
  
  **Other States**  
  
  Issuing **Send_Error** with the conversation in RESET or INITIALIZE state is illegal. The following return codes are possible:  
  
  CM_PROGRAM_PARAMETER_CHECK  
  Primary return code; the value specified by *conversation_ID* is invalid.  
  
  CM_PROGRAM_STATE_CHECK  
  Primary return code; the conversation state is not SEND, RECEIVE, CONFIRM, CONFIRM_SEND, CONFIRM_DEALLOCATE, or SEND_PENDING.  
  
  **State Changes**  
  
  The conversation can be in any state except INITIALIZE or RESET.  
  
  State changes, summarized in the following table, are based on the value of the *return_code* parameter.  
  
|*return_code*|New state|  
|--------------------|---------------|  
|CM_OK|SEND|  
|CM_CONVERSATION_TYPE_MISMATCH|RESET|  
|CM_PIP_NOT_SPECIFIED_CORRECTLY|RESET|  
|CM_SECURITY_NOT_VALID|RESET|  
|CM_SYNC_LEVEL_NOT_SUPPORTED_PGM|RESET|  
|CM_TPN_NOT_RECOGNIZED|RESET|  
|CM_TP_NOT_AVAILABLE_NO_RETRY|RESET|  
|CM_TP_NOT_AVAILABLE_RETRY|RESET|  
|CM_RESOURCE_FAILURE_RETRY|RESET|  
|CM_RESOURCE_FAILURE_NO_RETRY|RESET|  
|CM_DEALLOCATED_ABEND|RESET|  
|CM_DEALLOCATED_ABEND_PROG|RESET|  
|CM_DEALLOCATED_ABEND_SVC|RESET|  
|CM_DEALLOCATED_ABEND_TIMER|RESET|  
|CM_DEALLOCATED_NORMAL|RESET|  
|CM_PROGRAM_ERROR_PURGING|RECEIVE|  
CM_SVC_ERROR_PURGING|RECEIVE|  
|All others|No change|  
  
 Upon successful execution of this call, the conversation is in SEND state for the local program and in RECEIVE state for the partner program.  
  
 In a basic conversation, the local program can use [Set_Log_Data](../core/set-log-data-cpi-c-2.md) to specify that error log data be sent to the partner LU and added to the local error log. If the conversations log data length characteristic is greater than zero, the LU formats the data and stores it in the send buffer.  
  
 After **Send_Error** is completed, the log data length is set to zero and the log data to null.  
  
 If the conversation is in RECEIVE state when the program issues **Send_Error**, incoming data is purged by CPI-C. This data includes:  
  
- Data sent by [Send_Data](../core/send-data-cpi-c-2.md).  
  
- Confirmation requests.  
  
- Deallocation requests if the conversations deallocate type is set to CM_DEALLOCATE_CONFIRM or to CM_DEALLOCATE_SYNC_LEVEL with the synchronization level set to CM_CONFIRM.  
  
  CPI-C does notpurge an incoming request-to-send indicator.  
  
  If the conversation is in SEND_PENDING state, the local program can issue [Set_Error_Direction](../core/set-error-direction-cpi-c-1.md) to specify whether the error being reported resulted from the received data or from the processing of the local program after successfully receiving the data.  
  
## Remarks  
 The local program can use **Send_Error** for such purposes as informing the partner program of an error encountered in received data, rejecting a confirmation request, or truncating an incomplete logical record it is sending.  
  
 **Send_Error** flushes the local LUs send buffer and sends the partner program the contents of the send buffer followed by the error notification.  
  
 The error notification is sent to the partner as one of the following *return_code* values:  
  
-   CM_PROGRAM_ERROR_TRUNC  
  
-   CM_PROGRAM_ERROR_NO_TRUNC  
  
-   CM_PROGRAM_ERROR_PURGING