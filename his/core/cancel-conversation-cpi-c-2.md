---
description: "Learn more about: Cancel_Conversation (CPI-C)"
title: "Cancel_Conversation (CPI-C)2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Cancel_Conversation (CPI-C)
The **Cancel_Conversation** call (function name **cmcanc**) cancels any outstanding operation on a conversation (an operation returned with CM_OPERATION_INCOMPLETE) and the conversation itself.  
  
## Syntax  
  
```  
  
CM_ENTRY Cancel_Conversation(   
  unsigned char FAR *conversation_ID,    
    CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Returned parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
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
 The conversation must be in any state except RESET.  
  
 When the return code is CM_OK, the conversation state becomes RESET.  
  
## Remarks  
 **Cancel_Conversation** can be called while another operation is active for the specified *conversation_ID*. This allows an application to end any CPI-C action, but will terminate the conversation. This call can be issued regardless of the current application processing mode. Any outstanding operations will return with CM_DEALLOCATED_ABEND as the return code.  
  
 The conversation is terminated by a [Deallocate](../core/deallocate-cpi-c-1.md) with *deallocate_type* set to ABEND_SVC. No *log_data* is sent. The system may be unable to do this immediately, but any delay is transparent to the program.  
  
> [!NOTE]
>  If **Cancel_Conversation** is called while there are outstanding [Specify_Windows_Handle](../core/specify-windows-handle-cpi-c-2.md) asynchronous calls, these calls are canceled. The return codes are set to canceled, and a completion message is posted.
