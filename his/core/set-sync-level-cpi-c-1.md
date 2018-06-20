---
title: "Set_Sync_Level (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f514e271-c54c-41ae-8b72-581bbebb66e3
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Set_Sync_Level (CPI-C)
The **Set_Sync_Level** call (function name **cmssl**) is issued by the invoking program to specify the synchronization level of the conversation. The synchronization level determines whether the programs synchronize their processing through the [Confirm](../core/confirm-cpi-c-2.md) and [Confirmed](../core/confirmed-cpi-c-2.md) calls.  
  
 This call overrides the synchronization level established by the [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) call. The default synchronization level is CM_NONE, indicating no synchronization. This call cannot be issued after the [Allocate](../core/allocate-cpi-c-2.md) call has been issued.  
  
## Syntax  
  
```  
  
CM_ENTRY Set_Sync_Level(   
  unsigned char FAR *conversation_ID,    
  CM_INT32 FAR *sync_level,              
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by **Initialize_Conversation**.  
  
 *sync_level*  
 Supplied parameter. Specifies the synchronization level of the conversation. Possible values are:  
  
 CM_NONE  
 The programs will not perform confirmation processing.  
  
 CM_CONFIRM  
 The programs can perform confirmation processing.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_STATE_CHECK  
 Primary return code; the conversation is not in INITIALIZE state.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; one of the following occurred:  
  
- The value specified by *conversation_ID* or *sync_level* is invalid.  
  
- The *sync_level* parameter specifies CM_NONE but one of the following has occurred: the *send_type* parameter is set to CM_SEND_AND_CONFIRM, the *prepare_to_receive_type* parameter is set to CM_PREP_TO_RECEIVE_CONFIRM, or the *deallocate_type* is set to CM_DEALLOCATE_CONFIRM.  
  
  CM_PRODUCT_SPECIFIC_ERROR  
  Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation must be in INITIALIZE state.  
  
 There is no state change.