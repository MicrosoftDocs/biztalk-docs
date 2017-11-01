---
title: "Set_Receive_Type (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42bec64b-48b4-4c6d-92d3-dd8d434434cc
caps.latest.revision: 3
---
# Set_Receive_Type (CPI-C)
The **Set_Receive_Type** call (function name **cmsrt**) specifies how the program will receive data on subsequent [Receive](../core/receive-cpi-c.md) calls. It overrides the default receive type established by the [Initialize_Conversation](../core/initialize-conversation-cpi-c.md) or [Accept_Conversation](../core/accept-conversation-cpi-c.md) call. By default, the program waits for data to arrive if it is not available when the **Receive** call is issued.  
  
 The receive type value affects all subsequent **Receive** calls. It can be changed by reissuing **Set_Receive_Type**.  
  
## Syntax  
  
```  
  
CM_ENTRY Set_Receive_Type(   
  unsigned char FAR *conversation_ID,    
  CM_INT32 FAR *receive_type,            
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c.md) or [Accept_Conversation](../core/accept-conversation-cpi-c.md).  
  
 *receive_type*  
 Supplied parameter. Specifies how data is to be received by the program on the subsequent [Receive](../core/receive-cpi-c.md) calls. Possible values are:  
  
 CM_RECEIVE_AND_WAIT  
 The local program receives any data currently available from the partner program. If no data is available, the local program waits for data to arrive.  
  
 CM_RECEIVE_IMMEDIATE  
 The local program receives any data currently available from the partner program. If no data is available, the local program does not wait.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; the value specified by *conversation_ID* or *receive_type* is invalid, or the address of a variable is invalid.  
  
 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation can be in any state except RESET.  
  
 There is no state change.