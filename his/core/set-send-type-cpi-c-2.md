---
title: "Set_Send_Type (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 094eb433-40f5-4549-a1ee-eacff5753440
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Set_Send_Type (CPI-C)
The **Set_Send_Type** call (function name **cmsst**) specifies how data will be sent by the next [Send_Data](../core/send-data-cpi-c-2.md) call. It overrides the default send type established by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md). The default send type is CM_BUFFER_DATA, indicating that data only (and no control information) is to be sent.  
  
 The *send_type* value affects all subsequent **Send_Data** calls. It can be changed by reissuing **Set_Send_Type**.  
  
## Syntax  
  
```  
  
CM_ENTRY Set_Send_Type(   
  unsigned char FAR *conversation_ID,    
    CM_INT32 FAR *send_type,               
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 *send_type*  
 Supplied parameter. Specifies how data is sent by the next [Send_Data](../core/send-data-cpi-c-2.md) call. Possible values are:  
  
 CM_BUFFER_DATA  
 The data pointed to by **Send_Data** is stored in a buffer until the buffer fills up or is flushed.  
  
 CM_SEND_AND_FLUSH  
 The data pointed to by **Send_Data** is to be sent immediately.  
  
 CM_SEND_AND_CONFIRM  
 The data is to be sent immediately with a request for confirmation.  
  
 CM_SEND_AND_PREP_TO_RECEIVE  
 The data is to be sent immediately along with notification to the partner program that the conversation state for the sending program is changing to RECEIVE.  
  
 CM_SEND_AND_DEALLOCATE  
 The data is to be sent immediately along with deallocation notification.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; one of the following occurred:  
  
- The value specified by *conversation_ID* or *send_type* is invalid.  
  
- The *send_type* parameter is set to CM_SEND_AND_CONFIRM, but the conversations synchronization level is set to CM_NONE.  
  
  CM_PRODUCT_SPECIFIC_ERROR  
  Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
  **State Changes**  
  
  The conversation can be in any state except RESET.  
  
  There is no state change.  
  
## Remarks  
 The *send_type* values that cause additional information to be sent with the data pointed to by [Send_Data](../core/send-data-cpi-c-2.md) let you economize on the number of calls issued. The following table summarizes **Send_Data** equivalences.  
  
|Send_Data with *send_type* set to this value|Equates to Send_Data with *send_type* set to CM_BUFFER_DATA followed by|  
|----------------------------------------------------|---------------------------------------------------------------------------------|  
|CM_SEND_AND_FLUSH|[Flush](../core/flush-cpi-c-2.md)|  
|CM_SEND_AND_CONFIRM|[Confirm](../core/confirm-cpi-c-2.md)|  
|CM_SEND_AND_PREP_TO_RECEIVE|[Prepare_To_Receive](../core/prepare-to-receive-cpi-c-1.md)|  
|CM_SEND_AND_DEALLOCATE|[Deallocate](../core/deallocate-cpi-c-1.md)|