---
title: "Accept_Conversation (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d3282c5-04b7-42dd-91ea-b204f7ba47e5
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Accept_Conversation (CPI-C)
The **Accept_Conversation** call (function name **cmaccp**) is issued by the invoked program to accept the incoming conversation and set certain conversation characteristics. For a list of initial conversation characteristics, see [Initial Conversation Characteristics](../HIS2010/initial-conversation-characteristics2.md).  
  
## Syntax  
  
```  
  
CM_ENTRY Accept_Conversation(   
   unsigned char FAR *conversation_ID,    
      CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Returned parameter. Specifies the identifier for the conversation. It is used by subsequent CPI-C calls and is returned if the return code is either CM_OK or CM_OPERATION_INCOMPLETE. If the return code is CM_OPERATION_INCOMPLETE, the *conversation_ID* parameter can be used by the application to wait for or cancel the conversation.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_STATE_CHECK  
 Primary return code; there is no incoming conversation (blocking mode only), or no local transaction program (TP) name has been set up.  
  
 CM_OPERATION_INCOMPLETE  
 Primary return code; a nonblocking operation has been started on the conversation but is not complete. The program can issue [Wait_For_Conversation](../core/wait-for-conversation-cpi-c-1.md) to wait for the operation to complete or [Cancel_Conversation](../core/cancel-conversation-cpi-c-2.md) to cancel the operation and conversation.  
  
 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation must be in RESET state when **Accept_Conversation** is issued.  
  
 If the call is successful, the conversation changes to RECEIVE state. If the call fails, the state remains unchanged.  
  
## Remarks  
 Upon successful execution of this call, CPI-C generates an 8-byte conversation identifier. This identifier is a required parameter for all other CPI-C calls issued by the invoked program on this conversation.  
  
 Incoming conversations will be accepted according to the target TP name that they specify, which must match local TP names that have been set up. Local TP names can be set up by implementation-dependent methods, or by the program calling [Specify_Local_TP_Name](../core/specify-local-tp-name-cpi-c-2.md). In this way, a program can have more than one local TP name. The program can call [Extract_TP_Name](../core/extract-tp-name-cpi-c-2.md) to discover the name specified on the incoming conversation.  
  
 The operation is performed in nonblocking mode if the program has called **Specify_Local_TP_Name** previously; otherwise it is performed in blocking mode.