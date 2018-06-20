---
title: "Set_Deallocate_Type (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c89a7192-148c-4bbb-8124-493681e4852c
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Set_Deallocate_Type (CPI-C)
The **Set_Deallocate_Type** call (function name **cmsdt**) specifies how the conversation is to be deallocated.  
  
## Syntax  
  
```  
  
CM_ENTRY Set_Deallocate_Type(   
  unsigned char FAR *conversation_ID,    
  CM_INT32 FAR *deallocate_type,         
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 *deallocate_type*  
 Supplied parameter. Specifies how to perform the deallocation. Possible values are:  
  
 CM_DEALLOCATE_ABEND  
 Indicates that the conversation is to be deallocated abnormally and unconditionally. A program should specify CM_DEALLOCATE_ABEND when it encounters an error preventing the successful completion of a transaction.  
  
 If the conversation is in SEND state, CPI-C sends the contents of the send buffer of the local logical unit (LU) to the partner program before deallocating the conversation. If the conversation is in RECEIVE state, incoming data can be purged. For a basic conversation in SEND state, logical record truncation can occur.  
  
 CM_DEALLOCATE_CONFIRM  
 Used to send the partner program the contents of the local LUs send buffer and a request to confirm the deallocation.  
  
 This request for deallocation confirmation is sent by [Deallocate](../core/deallocate-cpi-c-1.md) or by [Send_Data](../core/send-data-cpi-c-2.md) with the send type set to CM_SEND_AND_DEALLOCATE. The conversation is deallocated normally when the partner program issues [Confirmed](../core/confirmed-cpi-c-2.md), responding to the confirmation request.  
  
 CM_DEALLOCATE_FLUSH  
 Used to send the contents of the local LUs send buffer to the partner program before deallocating the conversation normally.  
  
 CM_DEALLOCATE_SYNC_LEVEL  
 Uses the conversations synchronization level to determine how to deallocate the conversation. A default synchronization level is established by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) and can be overridden by [Set_Sync_Level](../core/set-sync-level-cpi-c-1.md).  
  
 If the synchronization level of the conversation is CM_NONE, the default, the contents of the local LUs send buffer are sent to the partner program and the conversation is deallocated normally.  
  
 If the synchronization level of the conversation is CM_CONFIRM, the contents of the local LUs send buffer and a request to confirm the deallocation are sent to the partner program. This request for deallocation confirmation is sent by [Deallocate](../core/deallocate-cpi-c-1.md) or by [Send_Data](../core/send-data-cpi-c-2.md) with the send type set to CM_SEND_AND_DEALLOCATE. The conversation is deallocated normally when the partner program issues the [Confirmed](../core/confirmed-cpi-c-2.md) call, responding to the confirmation request.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; one of the following occurred:  
  
- The value specified by *conversation_ID* or *deallocate_type* is invalid.  
  
- The *deallocate_type* parameter specifies CM_DEALLOCATE_CONFIRM, but the conversations synchronization level is set to CM_NONE.  
  
- The address of a variable is invalid.  
  
  CM_PRODUCT_SPECIFIC_ERROR  
  Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation can be in any state except RESET.  
  
 There is no state change.  
  
## Remarks  
 This call overrides the default deallocate type established by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md). The default deallocate type is CM_DEALLOCATE_SYNC_LEVEL.  
  
 The deallocation instructions specified by this call take effect when [Deallocate](../core/deallocate-cpi-c-1.md) is issued or when the send type is set to CM_SEND_AND_DEALLOCATE and [Send_Data](../core/send-data-cpi-c-2.md) is issued.  
  
 You can set *deallocate_type* to CM_FLUSH if the synchronization level of the conversation is set to CM_NONE or CM_CONFIRM.  
  
 The value CM_DEALLOCATE_FLUSH is functionally the same as CM_DEALLOCATE_SYNC_LEVEL with the conversations synchronization level set to CM_NONE.  
  
 The value CM_DEALLOCATE_CONFIRM is functionally the same as CM_DEALLOCATE_SYNC_LEVEL with the conversations synchronization level set to CM_CONFIRM.