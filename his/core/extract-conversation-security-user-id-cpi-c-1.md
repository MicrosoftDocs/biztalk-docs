---
description: "Learn more about: Extract_Conversation_Security_User_ID (CPI-C)"
title: "Extract_Conversation_Security_User_ID (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ce2941e6-aaf7-498e-b30c-64ac322059f3
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Extract_Conversation_Security_User_ID (CPI-C)
The **Extract_Conversation_Security_User_ID** call (function name **cmecsu**) returns the user identifier being used in a specified conversation.  
  
## Syntax  
  
```  
  
CM_ENTRY Extract_Conversation_Security_User_ID(   
  unsigned char FAR *conversation_ID,    
  unsigned char FAR *security_user_ID,    
  CM_INT32 FAR *security_user_ID_length,    
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 *security_user_ID*  
 Returned parameter. Specifies the user identifier that was used to establish the conversation.  
  
 *security_user_ID_length*  
 Returned parameter. Specifies the length of *security_user_ID*.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; the value specified by *conversation_ID* is invalid.  
  
## State Changes  
 The conversation can be in any state except RESET.  
  
 There is no state change.  
  
## Remarks  
 The *security_user_ID* value is not padded with spaces. It is meaningful only up to *security_user_ID_length*.
