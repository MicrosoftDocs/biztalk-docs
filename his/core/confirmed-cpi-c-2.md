---
title: "Confirmed (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ec1d382-8ef7-4064-a7b7-90203096a54b
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Confirmed (CPI-C)
The **Confirmed** call (function name **cmcfmd**) replies to a confirmation request from the partner program. It informs the partner program that the local program has not detected an error in the received data. Because the program issuing the confirmation request waits for a confirmation, **Confirmed** synchronizes the processing of the two programs.  

## Syntax  

```  

CM_ENTRY Confirmed(   
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
 Primary return code; the conversation was not in CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state when the program issued this call.  

 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error occurred and has been logged in the products error log.  

 **State Changes**  

 The conversation must be in one of the following states when the program issues **Confirmed**:  

- CONFIRM  

- CONFIRM_SEND  

- CONFIRM_DEALLOCATE  

  The new state is determined by the old state—the state of the conversation when the local program issued **Confirmed**. The old state is indicated by the *status_received* value of the preceding [Receive](../core/receive-cpi-c-2.md) call. The following table summarizes the possible state changes when *return_code* is set to CM_OK.  

|Old state|New state|  
|---------------|---------------|  
|CONFIRM|RECEIVE|  
|CONFIRM_SEND|SEND|  
|CONFIRM_DEALLOCATE|RESET|  

 Other return codes result in no state change.  

## Remarks  
 A confirmation request is issued by one of the following calls in the partner program:  

- [Confirm](../core/confirm-cpi-c-2.md).  

- [Prepare_To_Receive](../core/prepare-to-receive-cpi-c-1.md) if the prepare-to-receive type is set to CM_PREP_TO_RECEIVE_CONFIRM or to CM_PREP_TO_RECEIVE_SYNC_LEVEL and the conversations synchronization level is set to CM_CONFIRM.  

- [Deallocate](../core/deallocate-cpi-c-1.md) if the deallocate type is set to CM_DEALLOCATE_CONFIRM or to CM_DEALLOCATE_SYNC_LEVEL and the conversations synchronization level is set to CM_CONFIRM.  

- [Send_Data](../core/send-data-cpi-c-2.md) under the following circumstances:  

  -   The send type is set to CM_SEND_AND_CONFIRM.  

  -   The send type is set to CM_SEND_AND_PREPARE_TO_RECEIVE and the prepare-to-receive type is set to CM_PREPARE_TO_RECEIVE_CONFIRM.  

  -   The send type is set to CM_SEND_AND_PREPARE_TO_RECEIVE, the prepare-to-receive type is set to CM_PREPARE_TO_RECEIVE_SYNC_LEVEL, and the synchronization level is set to CM_CONFIRM.  

  -   The send type is set to CM_SEND_AND_DEALLOCATE and the deallocate type is set to CM_DEALLOCATE_CONFIRM.  

  -   The send type is set to CM_SEND_AND_DEALLOCATE, the deallocate type is set to CM_DEALLOCATE_SYNC_LEVEL, and the synchronization level is set to CM_CONFIRM.  

  A confirmation request is received by the local program through the *status_received* parameter of [Receive](../core/receive-cpi-c-2.md). The local program can issue **Confirmed** only if the *status_received* parameter is set to one of the following values:  

- CM_CONFIRM_RECEIVED  

- CM_CONFIRM_SEND_RECEIVED  

- CM_CONFIRM_DEALLOC_RECEIVED
