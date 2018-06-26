---
title: "Allocate (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3381c8c2-6d01-4f89-b023-03fcc2e5c7a0
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Allocate (CPI-C)
The **Allocate** call (function name **cmallc**) is issued by the invoking program to allocate a conversation with the partner program, using the current conversation characteristics. CPI-C can also allocate a session between the local logical unit (LU) and partner LU if one does not already exist.  
  
## Syntax  
  
```  
  
CM_ENTRY Allocate(   
  unsigned char FAR *conversation_ID,    
    CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the conversation identifier. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md).  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_OPERATION_NOT_ACCEPTED  
 Primary return code; this value indicates that a previous operation on this conversation is incomplete.  
  
 CM_OPERATION_INCOMPLETE  
 Primary return code; a nonblocking operation has been started on the conversation but is not complete. The program can issue [Wait_For_Conversation](../core/wait-for-conversation-cpi-c-1.md) to wait for the operation to complete or [Cancel_Conversation](../core/cancel-conversation-cpi-c-2.md) to cancel the operation and conversation.  
  
 CM_PARAMETER_ERROR  
 Primary return code; one of the following occurred:  
  
- The mode name derived from the side information or set by [Set_Mode_Name](../core/set-mode-name-cpi-c-2.md) is not valid.  
  
- The mode name is used by SNA service transaction programs (TPs); the invoking program does not have the authority to use this mode name. An example is SNASVCMG.  
  
- The partner program derived from the side information is an SNA service TP; the local program does not have the privilege required to allocate a conversation to an SNA service TP.  
  
- The partner program is a service TP, which participates in basic conversations, but the conversation is set to CM_MAPPED_CONVERSATION.  
  
- The partner LU name derived from the side information or set by [Set_Partner_LU_Name](../core/set-partner-lu-name-cpi-c-2.md) is not valid.  
  
  CM_PROGRAM_PARAMETER_CHECK  
  Primary return code; the value specified by *conversation_ID* is not valid, or the address of a variable is invalid.  
  
  CM_PROGRAM_STATE_CHECK  
  Primary return code; the conversation is not in INITIALIZE state.  
  
  CM_PRODUCT_SPECIFIC_ERROR  
  Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
  CM_UNSUCCESSFUL  
  Primary return code; the conversations return-control characteristic is set to CM_IMMEDIATE and the local LU did not have an available contention-winner session.  
  
  The following return codes can be generated if the conversations return-control type is set to CM_WHEN_SESSION_ALLOCATED.  
  
  CM_ALLOCATE_FAILURE_NO_RETRY  
  Primary return code; the conversation cannot be allocated because of a permanent condition, such as a configuration error or session protocol error. To determine the error, the system administrator should examine the error log file. Do not retry the allocation until the error has been corrected.  
  
  CM_ALLOCATE_FAILURE_RETRY  
  Primary return code; the conversation could not be allocated because of a temporary condition, such as a link failure. The reason for the failure is logged in the system error log. Retry the allocation.  
  
  **State Changes**  
  
  The conversation must be in INITIALIZE state when **Allocate** is issued.  
  
  State changes, summarized in the following table, are based on the value of the *return_code* parameter.  
  
|*return_code*|New state|  
|--------------------|---------------|  
|CM_OK|SEND|  
|CM_ALLOCATE_FAILURE_NO_RETRY|RESET|  
|CM_ALLOCATE_FAILURE_RETRY|RESET|  
|All others|No change|  
  
## Remarks  
 The type of conversation allocated is based on the conversation type characteristic: mapped or basic.  
  
 When the conversation has been allocated by this call, the following conversation characteristics cannot be changed:  
  
- Conversation type  
  
- Mode name  
  
- Partner LU name  
  
- Partner program name  
  
- Return control  
  
- Synchronization level  
  
- Conversation security  
  
- User identifier  
  
- Password  
  
  To send the allocation request immediately, the invoking program can issue [Flush](../core/flush-cpi-c-2.md) or [Confirm](../core/confirm-cpi-c-2.md) immediately after **Allocate**. Otherwise, the allocate request accumulates with other data in the local LUs send buffer until the buffer is full.  
  
  By issuing **Confirm** after **Allocate**, the invoking program can immediately determine whether the allocation was successful (if the conversation synchronization level is set to CM_CONFIRM).  
  
  If the partner LU rejects the allocation request generated by **Allocate**, the error is returned to the invoking program on a subsequent call.