---
title: "Request_To_Send (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fcb31fcb-59be-4bc8-8909-7df877cc8923
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Request_To_Send (CPI-C)
The **Request_To_Send** call (function name **cmrts**) notifies the partner program that the local program wants to send data.  
  
## Syntax  
  
```  
  
CM_ENTRY Request_To_Send(   
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
 Primary return code; the conversation is not in the RECEIVE, SEND, SEND_PENDING, CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state.  
  
 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation can be in any of the following states: RECEIVE, SEND, SEND_PENDING, CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE.  
  
 There is no state change.  
  
 In response to this request, the partner program can change the conversation to RECEIVE state by issuing one of the following calls:  
  
- [Receive](../core/receive-cpi-c-2.md) with receive type set to CM_RECEIVE_AND_WAIT  
  
- [Prepare_To_Receive](../core/prepare-to-receive-cpi-c-1.md)  
  
- **Send_Data** with send type set to CM_SEND_AND_PREP_TO_RECEIVE  
  
  The partner program can also ignore the request to send.  
  
  The conversation state changes to SEND for the local program when the local program receives one of the following values through the *status_received* parameter of a subsequent **Receive** call:  
  
- CM_SEND_RECEIVED  
  
- CM_CONFIRM_SEND_RECEIVED and the local program replies with a [Confirmed](../core/confirmed-cpi-c-2.md) call  
  
## Remarks  
 The request-to-send notification is received by the partner program through the *request_to_send_received* parameter of the following calls:  
  
- [Confirmed](../core/confirmed-cpi-c-2.md)  
  
- [Receive](../core/receive-cpi-c-2.md)  
  
- [Send_Data](../core/send-data-cpi-c-2.md)  
  
- [Send_Error](../core/send-error-cpi-c-2.md)  
  
- [Test_Request_To_Send_Received](../core/test-request-to-send-received-cpi-c-1.md)  
  
  Request-to-send notification is sent to the partner program immediately. CPI-C does not wait until the send buffer fills up or is flushed. Consequently, the request-to-send notification can arrive out of sequence. For example, if the local program is in SEND state and issues the [Prepare_To_Receive](../core/prepare-to-receive-cpi-c-1.md) call followed by the **Request_To_Send** call, the partner program, in RECEIVE state, can receive the request-to-send notification before it receives the send notification. For this reason, *request_to_send* can be reported to a program through the [Receive](../core/receive-cpi-c-2.md) call.  
  
  Upon receiving a request-to-send notification, the partner logical unit (LU) retains the notification until the partner issues a call that returns *request_to_send_received*. The LU keeps only one request-to-send notification per conversation. Thus the local program can issue more **Request_To_Send** calls than are explicitly handled by the partner transaction program (TP).