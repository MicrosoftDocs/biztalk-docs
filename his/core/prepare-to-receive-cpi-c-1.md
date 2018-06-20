---
title: "Prepare_To_Receive (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7490ee8-e237-4399-84f4-aa918b7b9d84
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Prepare_To_Receive (CPI-C)
The **Prepare_To_Receive** call (function name **cmptr**) changes the state of the conversation for the local program from SEND to RECEIVE.  
  
## Syntax  
  
```  
  
CM_ENTRY Prepare_To_Receive(   
  unsigned char FAR *conversation_ID,    
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
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
 Primary return code; the value specified by *conversation_ID* is invalid.  
  
 CM_PROGRAM_STATE_CHECK  
 Primary return code; one of the following occurred:  
  
- The conversation state is not SEND or SEND_PENDING.  
  
- For a basic conversation, the conversation is in SEND state. However, the program did not finish sending a logical record.  
  
  These return codes can occur if the conversations prepare-to-receive type is set to CM_PREP_TO_RECEIVE_CONFIRM or if the prepare-to-receive type is set to CM_PREP_TO_RECEIVE_SYNC_LEVEL and the conversations synchronization level is set to CM_CONFIRM.  
  
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
  
  The conversation can be in SEND or SEND_PENDING state.  
  
  State changes, summarized in the following table, are based on the value of the *return_code* parameter.  
  
|*return_code*|New state|  
|--------------------|---------------|  
|CM_OK|RECEIVE|  
|CM_PROGRAM_ERROR_PURGING|RECEIVE|  
|CM_SVC_ERROR_PURGING|RECEIVE|  
|CM_CONVERSATION_TYPE_MISMATCH|RESET|  
|CM_PIP_NOT_SPECIFIED_CORRECTLY|RESET|  
|CM_SECURITY_NOT_VALID|RESET|  
|CM_SYNC_LEVEL_NOT_SUPPORTED_PGM|RESET|  
|CM_TPN_NOT_RECOGNIZED|RESET|  
|CM_TP_NOT_AVAILABLE_NO_RETRY|RESET|  
|CM_TP_NOT_AVAILABLE_RETRY|RESET|  
|CM_DEALLOCATED_ABEND|RESET|  
|CM_RESOURCE_FAILURE_NO_RETRY|RESET|  
|CM_RESOURCE_FAILURE_RETRY|RESET|  
|CM_DEALLOCATED_ABEND_SVC|RESET|  
|CM_DEALLOCATED_ABEND_TIMER|RESET|  
|All others|No change|  
  
 Before changing the conversation state, this call performs the equivalent of one of the following:  
  
- The [Flush](../core/flush-cpi-c-2.md) call, sending the contents of the local LUs send buffer to the partner LU and program, if either of the following conditions is true:  
  
  -   The conversations prepare-to-receive type is set to CM_PREP_TO_RECEIVE_FLUSH.  
  
  -   The conversations prepare-to-receive type is set to CM_PREP_TO_RECEIVE_SYNC_LEVEL and the conversations synchronization level is set to CM_NONE.  
  
- The [Confirm](../core/confirm-cpi-c-2.md) call, sending the contents of the local LUs send buffer and a confirmation request to the partner program, if either of the following conditions is true:  
  
  -   The conversations prepare-to-receive type is set to CM_PREP_TO_RECEIVE_CONFIRM.  
  
  -   The conversations prepare-to-receive type is set to CM_PREP_TO_RECEIVE_SYNC_LEVEL and the conversations synchronization level is set to CM_CONFIRM.  
  
  The prepare-to-receive type is set by [Set_Prepare_To_Receive_Type](../core/set-prepare-to-receive-type-cpi-c-1.md); the synchronization level is set by [Set_Sync_Level](../core/set-sync-level-cpi-c-1.md).  
  
  The conversation cannot change to SEND or SEND_PENDING for the partner program until the partner program receives one of the following values through the *status_received* parameter of the [Receive](../core/receive-cpi-c-2.md) call:  
  
- CM_SEND_RECEIVED  
  
- CM_CONFIRM_SEND_RECEIVED and replies with the [Confirmed](../core/confirmed-cpi-c-2.md) or [Send_Error](../core/send-error-cpi-c-2.md) call  
  
## Remarks  
 After this call has successfully executed, the local program can receive data.