---
title: "CPI-C Common Return Codes2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19d2152b-5026-41c7-a063-3f73e84fadc0
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# CPI-C Common Return Codes
This section describes the return codes for Common Programming Interface for Communications (CPI-C) calls. The return codes are listed in integer order.  
  
 Call-specific return codes are described for the individual calls in [CPI-C Calls](../core/cpi-c-calls2.md).  
  
## 0  
 CM_OK  
 The call executed successfully.  
  
## 1  
 CM_ALLOCATION_FAILURE_NO_RETRY  
 The conversation cannot be allocated because of a permanent condition, such as a configuration error or session protocol error. To determine the error, the system administrator should examine the error log file. Do not retry the allocation until the error has been corrected.  
  
## 2  
 CM_ALLOCATION_FAILURE_RETRY  
 The conversation could not be allocated because of a temporary condition, such as a link failure. The reason for the failure is logged in the system error log. Retry the allocation.  
  
## 3  
 CM_CONVERSATION_TYPE_MISMATCH  
 The partner LU or program does not support the conversation type (basic or mapped) specified in the allocation request.  
  
## 5  
 CM_PIP_NOT_SPECIFIED_CORRECTLY  
 The allocation request was rejected by a non-CPI-C LU 6.2 transaction program (TP). The partner program requires one or more PIP data variables, which are not supported by CPI-C.  
  
## 6  
 CM_SECURITY_NOT_VALID  
 The user identifier or password specified in the allocation request was not accepted by the partner logical unit (LU).  
  
## 8  
 CM_SYNC_LVL_NOT_SUPPORTED_PGM  
 The partner program does not support the synchronization level specified in the allocation request.  
  
## 9  
 CM_TPN_NOT_RECOGNIZED  
 The partner LU does not recognize the program name specified in the allocation request.  
  
## 10  
 CM_TP_NOT_AVAILABLE_NO_RETRY  
 The partner LU cannot start the program specified in the allocation request because of a permanent condition. The reason for the error may be logged on the remote node. Do not retry the allocation until the error has been corrected.  
  
## 11  
 CM_TP_NOT_AVAILABLE_RETRY  
 The partner LU cannot start the program specified in the allocation request because of a temporary condition. The reason for the error may be logged on the remote node. Retry the allocation.  
  
## 17  
 CM_DEALLOCATED_ABEND  
 The conversation has been deallocated for one of the following reasons:  
  
-   The remote program issued [Deallocate](../core/deallocate-cpi-c-1.md) with the type parameter set to CM_DEALLOCATE_ABEND. If the conversation for the remote program was in RECEIVE state when the call was issued, information sent by the local program and not yet received by the remote program is purged.  
  
-   The partner program terminated normally but did not deallocate the conversation before terminating.  
  
## 18  
 CM_DEALLOCATED_NORMAL  
 This return code does not indicate an error.  
  
 The partner program issued the [Deallocate](../core/deallocate-cpi-c-1.md) call with *deallocate_type* set to one of the following:  
  
-   CM_DEALLOCATE_FLUSH.  
  
-   CM_DEALLOCATE_SYNC_LEVEL with the synchronization level of the conversation specified as CM_NONE.  
  
## 19  
 CM_PARAMETER_ERROR  
 The local program specified an invalid argument in one of its parameters.  
  
## 20  
 CM_PRODUCT_SPECIFIC_ERROR  
 A product-specific error occurred and has been logged in the products error log.  
  
## 21  
 CM_PROGRAM_ERROR_NO_TRUNC  
 While in SEND state or in SEND-PENDING state with the error direction set to CM_SEND_ERROR, the partner program issued [Send_Error](../core/send-error-cpi-c-2.md). Data was not truncated.  
  
## 22  
 CM_PROGRAM_ERROR_PURGING  
 One of the following occurred:  
  
-   While in RECEIVE or CONFIRM state, the partner program issued [Send_Error](../core/send-error-cpi-c-2.md). Data sent but not yet received is purged.  
  
-   While in SEND-PENDING state with the error direction set to CM_RECEIVE_ERROR, the partner program issued **Send_Error**. Data was not purged.  
  
## 23  
 CM_PROGRAM_ERROR_TRUNC (for a basic conversation)  
 In SEND state, before finishing sending a complete logical record, the partner program issued [Send_Error](../core/send-error-cpi-c-2.md). The local program may have received the first part of the logical record through a [Receive](../core/receive-cpi-c-2.md) call.  
  
## 24  
 CM_PROGRAM_PARAMETER_CHECK  
 A parameter or the address of a variable is invalid. For details, see individual calls in [CPI-C Calls](../core/cpi-c-calls2.md).  
  
## 25  
 CM_PROGRAM_STATE_CHECK  
 The call was not issued in an allowed conversation state. For details, see individual calls in [CPI-C Calls](../core/cpi-c-calls2.md).  
  
## 26  
 CM_RESOURCE_FAILURE_NO_RETRY  
 One of the following occurred:  
  
-   The conversation was terminated prematurely because of a permanent condition. Do not retry until the error has been corrected.  
  
-   The partner program did not deallocate the conversation before terminating normally.  
  
## 27  
 CM_RESOURCE_FAILURE_RETRY  
 The conversation was terminated prematurely because of a temporary condition, such as modem failure. Retry the conversation.  
  
## 28  
 CM_UNSUCCESSFUL  
 The verb issued by the local program was not executed successfully.  
  
## 30  
 CM_DEALLOCATED_ABEND_SVC  
 The conversation has been deallocated for one of the following reasons:  
  
- The partner program issued [Deallocate](../core/deallocate-cpi-c-1.md) with the type parameter set to ABEND_SVC.  
  
- The partner program did not deallocate the conversation before terminating.  
  
  If the conversation is in RECEIVE state for the partner program when this call is issued by the local program, data sent by the local program and not yet received by the partner program is purged.  
  
## 31  
 CM_DEALLOCATED_ABEND_TIMER  
 The conversation has been deallocated because the partner program issued [Deallocate](../core/deallocate-cpi-c-1.md) with the type parameter set to ABEND_TIMER. If the conversation is in RECEIVE state for the partner program when this call is issued by the local program, data sent by the local program and not yet received by the partner program is purged.  
  
## 32  
 CM_SVC_ERROR_NO_TRUNC (for a basic conversation)  
 While in SEND state, the partner program or partner LU issued [Send_Error](../core/send-error-cpi-c-2.md) with the typeparameter set to SVC. Data was not truncated.  
  
## 33  
 CM_SVC_ERROR_PURGING  
 While in SEND state, the partner program or partner LU issued [Send_Error](../core/send-error-cpi-c-2.md) with the type parameter set to SVC. Data sent to the partner program may have been purged.  
  
## 34  
 CM_SVC_ERROR_TRUNC (for a basic conversation)  
 While in RECEIVE or CONFIRM state, the partner program or partner LU issued [Send_Error](../core/send-error-cpi-c-2.md) with the type parameter set to SVC before it finished sending a complete logical record. The local program may have received the first part of the logical record.  
  
## 35  
 CM_OPERATION_INCOMPLETE  
 The operation has not completed and is still in progress. The program can issue [Wait_For_Conversation](../core/wait-for-conversation-cpi-c-1.md) to await the completion of the operation, or [Cancel_Conversation](../core/cancel-conversation-cpi-c-2.md) to cancel the operation and conversation. If [Specify_Windows_Handle](../core/specify-windows-handle-cpi-c-2.md) has been called, the application should wait for notification by a windows message and not call **Wait_For_Conversation**.  
  
## 36  
 CM_SYSTEM_EVENT  
 This error code is not used by Host Integration Server.  
  
## 37  
 CM_OPERATION_NOT_ACCEPTED  
 A previous operation on this conversation is incomplete.