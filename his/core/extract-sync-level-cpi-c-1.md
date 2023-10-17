---
description: "Learn more about: Extract_Sync_Level (CPI-C)"
title: "Extract_Sync_Level (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8570437-dca3-498d-b46e-217a1d056f0f
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Extract_Sync_Level (CPI-C)
The **Extract_Sync_Level** call (function name **cmesl**) returns the synchronization level for a specified conversation.  
  
## Syntax  
  
```  
  
CM_ENTRY Extract_Sync_Level(   
  unsigned char FAR *conversation_ID,    
  CM_INT32 FAR *sync_level,              
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 *sync_level*  
 Returned parameter. Indicates the synchronization level of the conversation. Possible values are:  
  
 CM_NONE  
 The programs will not perform confirmation processing.  
  
 CM_CONFIRM  
 The programs can perform confirmation processing.  
  
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
