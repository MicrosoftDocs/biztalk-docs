---
title: "Set_Error_Direction (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 688cce47-fb00-4e68-be9d-83f7fb047daf
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Set_Error_Direction (CPI-C)
The **Set_Error_Direction** call (function name **cmsed**) specifies whether a program detected an error while receiving data or while preparing to send data.  
  
## Syntax  
  
```  
  
CM_ENTRY Set_Error_Direction(   
  unsigned char FAR *conversation_ID,    
  CM_INT32 FAR *error_direction,         
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 *error_direction*  
 Supplied parameter. Specifies the direction in which data was flowing when the program encountered an error. Possible values are:  
  
- CM_RECEIVE_ERROR  
  
   An error occurred in the data received from the partner program.  
  
- CM_SEND_ERROR  
  
   An error occurred while the local program prepared to send data to the partner program.  
  
  *return_code*  
  The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; the value specified by *conversation_ID* or *error_direction* is invalid.  
  
 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation can be in any state except RESET.  
  
 There is no state change.  
  
## Remarks  
 This call overrides the default error direction established by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md). The default error direction is CM_RECEIVE_ERROR.  
  
 Error direction is relevant only when a program issues [Send_Error](../core/send-error-cpi-c-2.md) in SEND_PENDING state, immediately after issuing [Receive](../core/receive-cpi-c-2.md)and receiving data (*data_received* is a value other than CM_NO_DATA_RECEIVED) and a send indicator (*status_received* is CM_SEND_RECEIVED).  
  
 When the conversation is in SEND_PENDING state, the program issues **Send_Error** if it detects errors in the received data or if an error occurred while the local program prepared to send data. The program must supply the error direction information using **Set_Error_Direction** before issuing **Send_Error** because the logical unit (LU) cannot tell which kind of error occurred (receive or send). The new error direction remains in effect until a subsequent **Set_Error_Direction** changes it.  
  
 When **Send_Error** is issued, the partner program receives one of the following return codes:  
  
-   CM_PROGRAM_ERROR_PURGING if *error_direction* is set to CM_RECEIVE_ERROR  
  
-   CM_PROGRAM_ERROR_NO_TRUNC if *error_direction* is set to CM_SEND_ERROR