---
description: "Learn more about: Extract_TP_Name (CPI-C)"
title: "Extract_TP_Name (CPI-C)2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Extract_TP_Name (CPI-C)
The **Extract_TP_Name** call (function name **cmetpn**) returns the *TP_name* characteristic.  
  
## Syntax  
  
```  
  
CM_ENTRY Extract_TP_Name(   
  unsigned char FAR *conversation_ID,    
  unsigned char FAR *TP_name,            
  CM_INT32 FAR *TP_name_length,          
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 *TP_name*  
 Returned parameter. Specifies the variable containing the transaction program (TP) name.  
  
 *TP_name_length*  
 Returned parameter. Specifies the length of the TP name.  
  
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
  
## Remarks  
 For an invoking program, the *TP_name* characteristic is the value in the side information referenced in the *sym_dest_name* parameter of the [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) call. For an invokable program, it is the name specified in the conversation startup request (which will have been matched with a name specified locally or in a [Specify_Local_TP_Name](../core/specify-local-tp-name-cpi-c-2.md) call), and will therefore be the same as the *TP_name* characteristic of the partner program.  
  
 The name returned can be up to 64 bytes in length.
