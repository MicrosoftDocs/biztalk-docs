---
title: "Extract_Mode_Name (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a15c7db1-4b51-4edd-9ca3-64445f3a157d
caps.latest.revision: 3
---
# Extract_Mode_Name (CPI-C)
The **Extract_Mode_Name** call (function name **cmemn**) returns the mode name and mode name length for a specified conversation.  
  
## Syntax  
  
```  
  
CM_ENTRY Extract_Mode_Name(   
  unsigned char FAR *conversation_ID,    
  unsigned char FAR *mode_name,      
  CM_INT32 FAR *mode_name_length,    
  CM_INT32 FAR *return_code          
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../HIS2010/initialize-conversation-cpi-c-2.md) or [Accept_Conversation](../HIS2010/accept-conversation-cpi-c-1.md).  
  
 *mode_name*  
 Returned parameter. Specifies the starting address of the mode name.  
  
 *mode_name_length*  
 Returned parameter. Specifies the length of the mode name.  
  
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