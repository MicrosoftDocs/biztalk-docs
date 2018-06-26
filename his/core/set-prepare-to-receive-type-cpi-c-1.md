---
title: "Set_Prepare_To_Receive_Type (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4b8a136-8871-49a3-a6bd-ef2daf0333f6
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Set_Prepare_To_Receive_Type (CPI-C)
The **Set_Prepare_To_Receive_Type** call (function name **cmsptr**) specifies how the subsequent [Prepare_To_Receive](../core/prepare-to-receive-cpi-c-1.md) calls will be executed. It overrides the default prepare-to-receive processing established by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md). By default, the prepare-to-receive processing is based on the synchronization level of the conversation.  
  
 The prepare-to-receive type affects all subsequent **Prepare_To_Receive** calls. It can be changed by reissuing **Set_Prepare_To_Receive_Type**.  
  
## Syntax  
  
```  
  
CM_ENTRY Set_Prepare_To_Receive_Type(   
  unsigned char FAR *conversation_ID,    
  CM_INT32 FAR *prepare_to_receive_type,    
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 *prepare_to_receive_type*  
 Supplied parameter. Specifies how subsequent [Prepare_To_Receive](../core/prepare-to-receive-cpi-c-1.md) calls will be executed. Possible values are:  
  
 CM_PREP_TO_RECEIVE_CONFIRM  
 Used to send the partner program the contents of the send buffer of the logical unit (LU) and a confirmation request. Upon receipt of confirmation, the conversation changes to RECEIVE state.  
  
 CM_PREP_TO_RECEIVE_FLUSH  
 Used to send the partner program the contents of the local LUs send buffer and changes the conversation to RECEIVE state.  
  
 CM_PREP_TO_RECEIVE_SYNC_LEVEL  
 Used by the conversations synchronization level to determine prepare-to-receive processing. A default synchronization level is established by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) and can be overridden by [Set_Sync_Level](../core/set-sync-level-cpi-c-1.md).  
  
 If the synchronization level of the conversation is CM_NONE, the default, the contents of the local LUs send buffer are sent to the partner program and the conversation changes to RECEIVE state. If the synchronization level of the conversation is CM_CONFIRM, the contents of the local LUs send buffer and a request for confirmation are sent to the partner program. The conversation changes to RECEIVE state when the partner program issues [Confirmed](../core/confirmed-cpi-c-2.md), responding to the confirmation request.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; one of the following occurred:  
  
- The value specified by *prepare_to_receive_type* or *conversation_ID* is invalid.  
  
- The *prepare_to_receive_type* parameter is set to CM_PREP_TO_RECEIVE_CONFIRM, but the conversations synchronization level is set to CM_NONE.  
  
  CM_PRODUCT_SPECIFIC_ERROR  
  Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation can be in any state except RESET.  
  
 There is no state change.