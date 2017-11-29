---
title: "Extract_Partner_LU_Name (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9dfd0e40-5fde-4937-9d88-0b41a6ada8fc
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Extract_Partner_LU_Name (CPI-C)
The **Extract_Partner_LU_Name** call (function name **cmepln**) returns the partner LU name and partner LU name length for a specified conversation. This can be an alias name of up to eight bytes or a fully qualified network name of up to 17 bytes.  
  
## Syntax  
  
```  
  
CM_ENTRY Extract_Partner_LU_Name(   
  unsigned char FAR *conversation_ID,    
  unsigned char FAR *partner_LU_name,    
  CM_INT32 FAR *partner_LU_name_length,    
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c.md) or [Accept_Conversation](../core/accept-conversation-cpi-c.md).  
  
 *partner_LU_name*  
 Returned parameter. Specifies the variable containing the partner LU name. (The program must supply a pointer to a suitable variable.)  
  
 *partner_LU_name_length*  
 Returned parameter. Specifies the length of the partner LU name.  
  
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
 An invokable CPI-C transaction program (TP) will only receive the fully qualified network name upon successful completion of this function call. An invokable CPI-C TP  is unable to retrieve the alias name using this call.