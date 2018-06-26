---
title: "Receive (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 651f4be0-f098-4294-ba9d-790ff0b76d6c
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Receive (CPI-C)
The **Receive** call (function name **cmrcv**) receives any data currently available from the partner program. For Microsoft Windows, run a background thread for all CPI-C communications and preserve the foreground thread for user interface only.  
  
## Syntax  
  
```  
  
CM_ENTRY Receive(   
unsigned char FAR *conversation_ID,    
unsigned char FAR *buffer,             
CM_INT32 FAR *requested_length,        
CM_INT32 FAR *data_received,           
CM_INT32 FAR *received_length,         
CM_INT32 FAR *status_received,         
CM_INT32 FAR *request_to_send_received,    
CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 conversation_ID  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 buffer  
 Returned parameter. Specifies the address of the buffer to contain the data received by the local program.  
  
 The buffer contains data if the following conditions are true:  
  
- The *data_received* parameter is set to a value other than CM_NO_DATA_RECEIVED.  
  
- The *return_code* parameter is set to CM_OK or to CM_DEALLOCATED_NORMAL.  
  
  requested_length  
  Supplied parameter. Indicates the maximum number of bytes of data the local program is to receive. The range is from 0 through 32767.  
  
  data_received  
  Returned parameter. Indicates whether the program received data. Possible values are listed following the Parameters section.  
  
  received_length  
  Returned parameter. Indicates the number of bytes of data the local program received on this **Receive** call. If *return_code* or *data_received* indicates that the program received no data, this number is not relevant.  
  
  status_received  
  Returned parameter. Indicates changes in the status of the conversation. The following are possible values. These codes are not relevant unless *return_code* is set to CM_OK. Possible values are listed following the Parameters section.  
  
  request_to_send_received  
  Returned parameter. Specifies the request-to-send-received indicator. Values are listed following the Parameters section.  
  
  return_code  
  The code returned from this call. Values are listed following the Parameters section.  
  
## Values returned in the data_received parameter  
 These codes are not relevant unless *return_code* is set to CM_OK or CM_DEALLOCATED_NORMAL.  
  
 CM_DATA_RECEIVED  
 Can be returned for a basic conversation if the conversations fill characteristic is set to CM_FILL_BUFFER, indicating that the program is receiving data independent of its logical format. The local program received data until *requested_length* or end of data was reached.  
  
 The end of the data is indicated by either a change to another conversation state, based on the *return_code*, *status_received*, and *data_received* parameters, or an error condition. If the conversations receive type is set to CM_RECEIVE_IMMEDIATE, the data received can be less than *requested_length* if a smaller amount of data has arrived from the partner program.  
  
 CM_COMPLETE_DATA_RECEIVED  
 In a mapped conversation, indicates that the local program has received a complete data record or the last part of a data record.  
  
 In a basic conversation with the fill characteristic set to CM_FILL_LL, this value indicates that the local program has received a complete logical record or the end of a logical record.  
  
 CM_INCOMPLETE_DATA_RECEIVED  
 In a mapped conversation, indicates that the local program has received an incomplete data record. The *requested_length* parameter specified a value less than the length of the data record (or less than the remainder of the data record if this is not the first **Receive** to read the record). The amount of data received is equal to the *requested_length* parameter.  
  
 In a basic conversation with the fill characteristic set to CM_FILL_LL, this value indicates that the local program has received an incomplete logical record. The amount of data received is equal to the *requested_length* parameter. (If the received data was truncated, the length of the data will be less than *requested_length*.)  
  
 Upon receiving this value, the local program normally reissues **Receive** to receive the next part of the record.  
  
 CM_NO_DATA_RECEIVED  
 The program did not receive data.  
  
 Note that if the *return_code* parameter is set to CM_OK, status information may be available through the *status_received* parameter.  
  
## Values returned in the status_received parameter  
 CM_NO_STATUS_RECEIVED  
 No conversation status change was received on this call.  
  
 CM_SEND_RECEIVED  
 Indicates, for the partner program, that the conversation has entered RECEIVE state. For the local program, the conversation is now in SEND state if no data was received on this call, or SEND_PENDING state if data was received on this call.  
  
 Upon receiving this value, the local program normally uses [Send_Data](../core/send-data-cpi-c-2.md) to begin sending data.  
  
 CM_CONFIRM_DEALLOC_RECEIVED  
 Indicates that the partner program issued [Deallocate](../core/deallocate-cpi-c-1.md) with confirmation requested. For the local program, the conversation is now in CONFIRM_DEALLOCATE state.  
  
 Upon receiving this value, the local program normally issues the [Confirmed](../core/confirmed-cpi-c-2.md) call.  
  
 CM_CONFIRM_RECEIVED  
 Indicates that the partner program issued the [Confirm](../core/confirm-cpi-c-2.md) call. For the local program, the conversation is in CONFIRM state.  
  
 Upon receiving this value, the local program normally issues the **Confirmed** call.  
  
 CM_CONFIRM_SEND_RECEIVED  
 Indicates, for the partner program, that the conversation has entered RECEIVE state and a request for confirmation has been received by the local program. For the local program, the conversation is now in CONFIRM_SEND state.  
  
 The program normally responds by issuing the **Confirmed** call. Upon successful execution of the **Confirmed** call, the conversation changes to SEND state for the local program.  
  
## Values returned in the request_to_send_received parameter  
 CM_REQ_TO_SEND_RECEIVED  
 The partner program issued the [Request_To_Send](../core/request-to-send-cpi-c-1.md) call, which requests the local program to change the conversation to RECEIVE state.  
  
 CM_REQ_TO_SEND_NOT_RECEIVED  
 The partner program did not issue the **Request_To_Send** call. This value is not relevant if the *return_code* parameter is set to CM_PROGRAM_PARAMETER_CHECK or CM_PROGRAM_STATE_CHECK.  
  
## Values returned in the return_code parameter  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_OPERATION_NOT_ACCEPTED  
 Primary return code; a previous operation on this conversation is incomplete.  
  
 CM_OPERATION_INCOMPLETE  
 Primary return code; the operation has not completed (processing mode is nonblocking only) and is still in progress. The program can issue [Wait_For_Conversation](../core/wait-for-conversation-cpi-c-1.md) to await the completion of the operation, or [Cancel_Conversation](../core/cancel-conversation-cpi-c-2.md) to cancel the operation and conversation. If [Specify_Windows_Handle](../core/specify-windows-handle-cpi-c-2.md) has been called, the application should wait for notification by a Windows® message and not call **Wait_For_Conversation**.  
  
 CM_UNSUCCESSFUL  
 Primary return code; the receive type is set to CM_RECEIVE_IMMEDIATE and no data is immediately available from the partner program.  
  
 CM_DEALLOCATED_NORMAL  
 Primary return code; the conversation has been deallocated normally. The partner program issued [Deallocate](../core/deallocate-cpi-c-1.md) with the conversations deallocate type set to CM_DEALLOCATE_FLUSH or CM_DEALLOCATE_SYNC_LEVEL with the synchronization level of the conversation specified as CM_NONE.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; one of the following occurred:  
  
- The value specified by *conversation_ID* is invalid.  
  
- The value specified by *requested_length* is out of range (greater than 32767).  
  
  If the program receives this return code, the other returned parameters are not valid.  
  
  CM_PROGRAM_STATE_CHECK  
  Primary return code; one of the following occurred:  
  
- The receive type is set to CM_RECEIVE_AND_WAIT and the conversation state is not RECEIVE, SEND, or SEND_PENDING.  
  
- The receive type is set to CM_RECEIVE_IMMEDIATE and the conversation state is not RECEIVE.  
  
- In a basic conversation, the conversation is in SEND state, the receive type is set to CM_RECEIVE_AND_WAIT, and the program did not finish sending a logical record.  
  
  If the program receives this return code, the other returned parameters are not valid.  
  
  CM_PRODUCT_SPECIFIC_ERROR  
  Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
  CM_CONVERSATION_TYPE_MISMATCH  
  Primary return code; the partner logical unit (LU) or program does not support the conversation type (basic or mapped) specified in the allocation request.  
  
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
  
  CM_PROGRAM_ERROR_NO_TRUNC  
  Primary return code; while in SEND state or in SEND_PENDING state with the error direction set to CM_SEND_ERROR, the partner program issued [Send_Error](../core/send-error-cpi-c-2.md). Data was not truncated.  
  
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
  
- The remote program issued [Deallocate](../core/deallocate-cpi-c-1.md) with the type parameterset to CM_DEALLOCATE_ABEND, or the remote LU did so because of a remote program abnormal-ending condition. If the conversation for the remote program was in RECEIVE state when the call was issued, information sent by the local program and not yet received by the remote program is purged.  
  
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
  
  CM_SVC_ERROR_NO_TRUNC  
  Primary return code; while in SEND state, the partner program or partner LU issued **Send_Error** with the type parameter set to SVC. Data sent to the partner program may have been purged.  
  
  CM_PROGRAM_ERROR_TRUNC  
  Primary return code; in SEND state, before finishing sending a complete logical record, the partner program issued **Send_Error**. The local program may have received the first part of the logical record through a **Receive** call.  
  
  CM_SVC_ERROR_TRUNC  
  Primary return code; while in RECEIVE or CONFIRM state, the partner program or partner LU issued **Send_Error** with the type parameter set to SVC before it finished sending a complete logical record. The local program may have received the first part of the logical record.  
  
  **State Changes**  
  
  The conversation can be in RECEIVE, SEND, or SEND_PENDING state.  
  
  If *receive_type* is set to CM_RECEIVE_IMMEDIATE, the conversation must be in RECEIVE state.  
  
  Issuing **Receive** while the conversation is in SEND or SEND_PENDING state causes the local LU to send the information in its send buffer and a send indicator to the partner program. Based on *data_received* and *status_received* the conversation can change to RECEIVE state for the local program.  
  
  The new conversation state is determined by:  
  
- The state the conversation is in when the program issues the call.  
  
- The *return_code* parameter.  
  
- The data_received and status_received parameters.  
  
  If no data is currently available and the receive type (set by [Set_Receive_Type](../core/set-receive-type-cpi-c-2.md)) is set to CM_RECEIVE_AND_WAIT, the local program waits for data to arrive. If the receive type is set to CM_RECEIVE_IMMEDIATE, the local program does not wait.  
  
  The process for receiving data is as follows:  
  
- The local program issues a Receive call until it finishes receiving a complete unit of data. The local program may need to issue Receive several times to receive a complete unit of data. The *data_received* parameter indicates whether the receipt of data is finished.  
  
   The data received can be:  
  
  - One data record transmitted in a mapped conversation.  
  
  - One logical record transmitted in a basic conversation with the conversations fill characteristic set to CM_FILL_LL.  
  
  - A buffer of data received independent of its logical-record format in a basic conversation with the fill characteristic set to CM_FILL_BUFFER.  
  
    When a complete unit of data has been received, the local program can manipulate it.  
  
- The local program determines the next action to take based on the control information received through *status_received*. The local program may have to reissue **Receive** to receive the control information.  
  
  The conversation type is set by [Set_Conversation_Type](../core/set-conversation-type-cpi-c-1.md). The fill characteristic is set by [Set_Fill](../core/set-fill-cpi-c-1.md).  
  
  The following table summarizes the state changes that can occur when **Receive** is issued with the conversation in RECEIVE state and *return_code* is CM_OK.  
  
|*data_received*|*status_received*|New state|  
|----------------------|------------------------|---------------|  
|CM_DATA_RECEIVED|CM_NO_STATUS_RECEIVED|No change|  
|CM_COMPLETE_DATA_ RECEIVED|CM_NO_STATUS_RECEIVED|No change|  
|CM_INCOMPLETE_DATA_ RECEIVED|CM_SEND_RECEIVED|SEND_PENDING|  
|CM_NO_DATA_RECEIVED|CM_SEND_RECEIVED|SEND|  
  
 If *return_code* is set to CM_UNSUCCESSFUL, meaning that the *receive_type* is set to CM_RECEIVE_IMMEDIATE and no data is available, there is no state change.  
  
 The following table summarizes the state changes that can occur when **Receive** is issued with the conversation in SEND state and *return_code* is CM_OK.  
  
|*data_received*|*status_received*|New state|  
|----------------------|------------------------|---------------|  
|CM_DATA_RECEIVED|CM_NO_STATUS_RECEIVED|RECEIVE|  
|CM_COMPLETE_DATA_ RECEIVED|CM_NO_STATUS_RECEIVED|RECEIVE|  
|CM_INCOMPLETE_DATA_ RECEIVED|CM_SEND_RECEIVED|SEND_PENDING|  
|CM_NO_DATA_RECEIVED|CM_SEND_RECEIVED|No change|  
  
 The following table summarizes the state changes that can occur when **Receive** is issued with the conversation in SEND_PENDING state and *return_code* is CM_OK.  
  
|*data_received*|*status_received*|New state|  
|----------------------|------------------------|---------------|  
|CM_DATA_RECEIVED|CM_NO_STATUS_RECEIVED|RECEIVE|  
|CM_COMPLETE_DATA_ RECEIVED|CM_NO_STATUS_RECEIVED|RECEIVE|  
|CM_INCOMPLETE_DATA_ RECEIVED|CM_SEND_RECEIVED|No change|  
|CM_NO_DATA_RECEIVED|CM_SEND_RECEIVED|SEND|  
  
 The following topics summarize state changes that can occur when **Receive** is issued in any allowed state.  
  
## In This Section  
  
-   [Confirmation](../core/confirmation-cpi-c-1.md)  
  
-   [Normal Deallocation](../core/normal-deallocation-cpi-c-1.md)  
  
-   [ABEND](../core/abend-cpi-c-2.md)  
  
-   [Errors](../core/errors-cpi-c-1.md)