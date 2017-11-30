---
title: "Set_Conversation_Type (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4f81a853-b7bc-4d74-bd30-fc18553d8345
caps.latest.revision: 3
---
# Set_Conversation_Type (CPI-C)
The **Set_Conversation_Type** call (function name **cmsct**) is issued by the invoking program to define a conversation as being mapped or basic. This call overrides the default conversation type established by [Initialize_Conversation](../HIS2010/initialize-conversation-cpi-c-2.md). The default conversation type is CM_MAPPED_CONVERSATION. This call cannot be issued after [Allocate](../HIS2010/allocate-cpi-c-1.md) has been issued.  
  
## Syntax  
  
```  
  
CM_ENTRY Set_Conversation_Type(   
  unsigned char FAR *conversation_ID,    
  CM_INT32 FAR *conversation_type,    
    CM_INT32 FAR *return_code           
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../HIS2010/initialize-conversation-cpi-c-2.md).  
  
 *conversation_type*  
 Supplied parameter. Specifies the type of conversation to be allocated by **Allocate**. Possible values are:  
  
-   CM_BASIC_CONVERSATION  
  
-   CM_MAPPED_CONVERSATION  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_STATE_CHECK  
 Primary return code; the conversation is not in INITIALIZE state.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; one of the following occurred:  
  
-   The value specified by *conversation_ID* or *conversation_type* is invalid.  
  
-   The *conversation_type* parameter specifies a mapped conversation, but the fill characteristic is set to CM_FILL_BUFFER, which is incompatible with mapped conversations. Before changing the conversation type to mapped, you must issue the [Set_Fill](../HIS2010/set-fill-cpi-c-2.md) call to change the fill type to CM_FILL_LL.  
  
-   The *conversation_type* parameter specifies a mapped conversation. However, a previous [Set_Log_Data](../HIS2010/set-log-data-cpi-c-1.md) call, allowed only in basic conversations, is still in effect.  
  
 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation must be in INITIALIZE state.  
  
 There is no state change.