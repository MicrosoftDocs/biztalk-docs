---
title: "Extract_Conversation_State (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 421f5c62-c434-4866-8379-50b7fe145a24
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Extract_Conversation_State (CPI-C)
The **Extract_Conversation_State** call (function name **cmecs**) returns the state of the specified conversation.  
  
## Syntax  
  
```  
  
CM_ENTRY Extract_Conversation_State(   
  unsigned char FAR *conversation_ID,    
  CM_INT32 FAR *conversation_state,    
  CM_INT32 FAR *return_code            
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 *conversation_state*  
 Returned parameter. Specifies the conversation state. Possible values are:  
  
- CM_INITIALIZE_STATE  
  
- CM_SEND_STATE  
  
- CM_RECEIVE_STATE  
  
- CM_SEND_PENDING_STATE  
  
- CM_CONFIRM_STATE  
  
- CM_CONFIRM_SEND_STATE  
  
- CM_CONFIRM_DEALLOCATE_STATE  
  
  *return_code*  
  The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; the value specified by *conversation_ID* is invalid.  
  
 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation can be in any state except RESET.  
  
 There is no state change.