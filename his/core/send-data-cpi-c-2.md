---
title: "Send_Data (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 859def19-967a-4999-8b7c-0378d0a3cb68
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Send_Data (CPI-C)
The **Send_Data** call (function name **cmsend**) puts data in the send buffer of the local logical unit (LU) for transmission to the partner program.  
  
## Syntax  
  
```  
  
CM_ENTRY Send_Data(   
  unsigned char FAR *conversation_ID,    
  unsigned char FAR *buffer,             
    CM_INT32 FAR *send_length,             
    CM_INT32 FAR *request_to_send_received,    
    CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 *buffer*  
 Supplied parameter. Specifies the address of the buffer containing the data to be put in the local LUs send buffer.  
  
 *send_length*  
 Supplied parameter. Specifies the number of bytes of data to be put in the local LUs send buffer. The range is from 0 through 32767.  
  
 For a mapped conversation, if *send_length* is set to zero, a null data record is sent to the partner program.  
  
 For a basic conversation, if *send_length* is set to zero, no data is sent. The *buffer* parameter is not relevant. However, the other parameters are processed.  
  
 *request_to_send_received*  
 Returned parameter. It is the request-to-send-received indicator. Possible values are:  
  
 CM_REQ_TO_SEND_RECEIVED  
 The partner program issued the [Request_To_Send](../core/request-to-send-cpi-c-1.md) call, which requests the local program to change the conversation to RECEIVE state.  
  
 CM_REQ_TO_SEND_NOT_RECEIVED  
 The partner program did not issue the **Request_To_Send** call. This value is not relevant if *return_code* is set to CM_PROGRAM_PARAMETER_CHECK or CM_PROGRAM_STATE_CHECK.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_OPERATION_NOT_ACCEPTED  
 Primary return code; a previous operation on this conversation is incomplete.  
  
 CM_OPERATION_INCOMPLETE  
 Primary return code; the operation has not completed (processing mode is nonblocking only) and is still in progress. The program can issue [Wait_For_Conversation](../core/wait-for-conversation-cpi-c-1.md) to await the completion of the operation, or [Cancel_Conversation](../core/cancel-conversation-cpi-c-2.md) to cancel the operation and conversation. If [Specify_Windows_Handle](../core/specify-windows-handle-cpi-c-2.md) has been called, the application should wait for notification by a Microsoft® Windows® message and not call **Wait_For_Conversation**.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; one of the following occurred:  
  
- The value specified by *conversation_ID* is invalid.  
  
- The value specified by *send_length* is out of range (greater than 32767).  
  
- This is a basic conversation and the first two bytes of *buffer* contain an invalid logical record length (0x0000, 0x0001, 0x8000, or 0x8001).  
  
  CM_PROGRAM_STATE_CHECK  
  Primary return code; one of the following occurred:  
  
- The conversation state is not SEND or SEND_PENDING.  
  
- The basic conversation is in SEND state and *send_type* is set to CM_SEND_AND_CONFIRM, CM_SEND_AND_DEALLOCATE, or CM_SEND_AND_PREP_TO_RECEIVE. However, the data does not end on a logical record boundary. This condition is allowed only when *deallocate_type* is set to CM_DEALLOCATE_ABEND and the *send_type* is set to CM_SEND_AND_DEALLOCATE.  
  
  CM_PRODUCT_SPECIFIC_ERROR  
  Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
  CM_CONVERSATION_TYPE_MISMATCH  
  Primary return code; the partner LU or program does not support the conversation type (basic or mapped) specified in the allocation request.  
  
  CM_PIP_NOT_SPECIFIED_CORRECTLY  
  Primary return code; the allocation request was rejected by a non-CPI-C LU 6.2 transaction program (TP). The partner program requires one or more PIP data variables, which are not supported by CPI-C.  
  
  CM_SECURITY_NOT_VALID  
  Primary return code; the user identifier or password specified in the allocation request was not accepted by the partner LU.  
  
  CM_SYNC_LEVEL_NOT_SUPPORTED_PGM  
  Primary return code; the partner program does not support the synchronization level specified in the allocation request.  
  
  CM_TPN_NOT_RECOGNIZED  
  Primary return code; the partner LU does not recognize the program name specified in the allocation request.  
  
  CM_TP_NOT_AVAILABLE_NO_RETRY  
  Primary return code; the partner LU cannot start the program specified in the allocation request because of a permanent condition. The reason for the error may be logged on the remote node. Do not retry the allocation until the error has been corrected.  
  
  CM_TP_NOT_AVAILABLE_RETRY  
  Primary return code; the partner LU cannot start the program specified in the allocation request because of a temporary condition. The reason for the error may be logged on the remote node. Retry the allocation.  
  
  CM_PROGRAM_ERROR_PURGING  
  Primary return code; one of the following occurred:  
  
- While in RECEIVE or CONFIRM state, the partner program issued [Send_Error](../core/send-error-cpi-c-2.md). Data sent but not yet received is purged.  
  
- While in SEND_PENDING state with the error direction set to CM_RECEIVE_ERROR, the partner program issued **Send_Error**. Data was not purged.  
  
  CM_RESOURCE_FAILURE_NO_RETRY  
  Primary return code; one of the following occurred:  
  
- The conversation was terminated prematurely because of a permanent condition. Do not retry until the error has been corrected.  
  
- The partner program did not deallocate the conversation before terminating normally.  
  
  CM_RESOURCE_FAILURE_RETRY  
  Primary return code; the conversation was terminated prematurely because of a temporary condition, such as modem failure. Retry the conversation.  
  
  CM_DEALLOCATED_ABEND  
  Primary return code; the conversation has been deallocated for one of the following reasons:  
  
- The remote program issued [Deallocate](../core/deallocate-cpi-c-1.md) with the type parameter set to CM_DEALLOCATE_ABEND, or the remote LU did so because of a remote program abnormal-ending condition. If the conversation for the remote program was in RECEIVE state when the call was issued, information sent by the local program and not yet received by the remote program is purged.  
  
- The remote TP terminated normally but did not deallocate the conversation before terminating. Node services at the remote LU deallocated the conversation on behalf of the remote TP.  
  
  CM_DEALLOCATED_ABEND_SVC  
  Primary return code; the conversation has been deallocated for one of the following reasons:  
  
- The partner program issued **Deallocate** with the type parameter set to ABEND_SVC.  
  
- The partner program did not deallocate the conversation before terminating.  
  
  If the conversation is in RECEIVE state for the partner program when this call is issued by the local program, data sent by the local program and not yet received by the partner program is purged.  
  
  CM_DEALLOCATED_ABEND_TIMER  
  Primary return code; the conversation has been deallocated because the partner program issued **Deallocate** with the type parameter set to ABEND_TIMER. If the conversation is in RECEIVE state for the partner program when this call is issued by the local program, data sent by the local program and not yet received by the partner program is purged.  
  
  CM_SVC_ERROR_PURGING  
  Primary return code; while in SEND state, the partner program or partner LU issued [Send_Error](../core/send-error-cpi-c-2.md) with the type parameter set to SVC. Data sent to the partner program may have been purged.  
  
  **State Changes**  
  
  The conversation must be in SEND or SEND_PENDING state when the program issues this call.  
  
  The following table summarizes state changes that are possible when *return_code* is set to CM_OK.  
  
|*send_type*|Old state|New state|  
|------------------|---------------|---------------|  
|CM_BUFFER_DATA|SEND|No change|  
|CM_BUFFER_DATA|SEND_PENDING|SEND|  
|CM_SEND_AND_FLUSH|SEND|No change|  
|CM_SEND_AND_FLUSH|SEND_PENDING|SEND|  
|CM_SEND_AND_CONFIRM|SEND|No change|  
|CM_SEND_AND_CONFIRM|SEND_PENDING|SEND|  
|CM_SEND_AND_PREP_TO_ RECEIVE|Not available|RECEIVE|  
|CM_SEND_AND_DEALLOCATE|Not available|RESET|  
  
 For a *return_code* value of CM_PROGRAM_ERROR_PURGING or CM_SVC_ERROR_PURGING, the conversation changes to RECEIVE state. For other non-CM_OK values, the conversation changes to RESET state.  
  
## Remarks  
 The data collected in the local LUs send buffer is transmitted to the partner LU and partner program when one of the following occurs:  
  
- The send buffer fills up.  
  
- The local program issues a [Flush](../core/flush-cpi-c-2.md), [Confirm](../core/confirm-cpi-c-2.md), or [Deallocate](../core/deallocate-cpi-c-1.md) call or other call that flushes the LUs send buffer. (Some send types, set by [Set_Send_Type](../core/set-send-type-cpi-c-2.md), include flush functionality.)  
  
  The data to be sent can be either:  
  
- A complete data record on a mapped conversation. A complete data record is a string of the length specified by the *send_length* parameter.  
  
- A complete logical record or portion thereof on a basic conversation. A complete logical record is determined by the LL value. (One logical record can end and a new one begin in the middle of the string of data to be sent.)  
  
  The LU does not automatically perform any conversion between ASCII and EBCDIC on the string of data to be sent. If necessary, the program can use the Common Service Verb (CSV) [CONVERT](../core/convert2.md) to translate a string from one character set to the other.