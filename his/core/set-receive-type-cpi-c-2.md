---
description: "Learn more about: Set_Receive_Type (CPI-C)"
title: "Set_Receive_Type (CPI-C)2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
---
# Set_Receive_Type (CPI-C)
The **Set_Receive_Type** call (function name **cmsrt**) specifies how the program will receive data on subsequent [Receive](../core/receive-cpi-c-2.md) calls. It overrides the default receive type established by the [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md) call. By default, the program waits for data to arrive if it is not available when the **Receive** call is issued.  
  
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
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 *receive_type*  
 Supplied parameter. Specifies how data is to be received by the program on the subsequent [Receive](../core/receive-cpi-c-2.md) calls. Possible values are:  
  
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
