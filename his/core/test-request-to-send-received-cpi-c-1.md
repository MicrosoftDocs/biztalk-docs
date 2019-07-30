---
title: "Test_Request_To_Send_Received (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ce35a2d-838b-49c6-879f-e102adc9c0d8
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Test_Request_To_Send_Received (CPI-C)
The **Test_Request_To_Send_Received** call (function name **cmtrts**) determines whether a request-to-send notification has been received from the partner program.  
  
## Syntax  
  
```  
  
CM_ENTRY Test_Request_To_Send_Received(   
  unsigned char FAR *conversation_ID,    
  CM_INT32 FAR *request_to_send_received,    
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 *request_to_send_received*  
 Returned parameter. The request-to-send-received indicator. Possible values are:  
  
 CM_REQ_TO_SEND_RECEIVED  
 The partner program issued [Request_To_Send](../core/request-to-send-cpi-c-1.md), which requests the local program to change the conversation to RECEIVE state.  
  
 CM_REQ_TO_SEND_NOT_RECEIVED  
 The partner program did not issue **Request_To_Send**. This value is not relevant if *return_code* contains a value other than CM_OK.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; the value specified by *conversation_ID* is invalid, or the address of a variable is invalid.  
  
 CM_PROGRAM_STATE_CHECK  
 Primary return code; the conversation is in a state other than SEND, RECEIVE, or SEND_PENDING.  
  
 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation must be in SEND, RECEIVE, or SEND_PENDING state.  
  
 There is no state change.