---
title: "Extract_Conversation_Security_Type (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bd47d70d-7485-425f-b296-508f1931f452
caps.latest.revision: 3
---
# Extract_Conversation_Security_Type (CPI-C)
The **Extract_Conversation_Security_Type** call (function name **xcecst**) returns the security type for a specified conversation.  
  
## Syntax  
  
```  
  
CM_ENTRY Extract_Conversation_Security_Type(   
  unsigned char FAR *conversation_ID,          
    CM_INT32 FAR *conversation_security_type,    
    CM_INT32 FAR *return_code                    
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../HIS2010/initialize-conversation-cpi-c-2.md) or [Accept_Conversation](../HIS2010/accept-conversation-cpi-c-1.md).  
  
 *conversation_security_type*  
 Returned parameter. Specifies the information the partner logical unit (LU) requires to validate access to the invoked program. Possible values are:  
  
 CM_SECURITY_NONE  
 The invoked program uses no conversation security.  
  
 CM_SECURITY_PROGRAM  
 The invoked program uses conversation security and thus requires a user identifier and password.  
  
 CM_SECURITY_SAME  
 The invoked program, invoked with a valid user identifier and password, in turn invokes another program (as illustrated in [Communication Between TPs](../HIS2010/communication-between-tps-cpi-c-1.md)). For example, assume that program A invokes program B with a valid user identifier and password, and program B in turn invokes program C. If program B specifies the value CM_SECURITY_SAME, CPI-C sends the LU for program C, the user identifier from program A, and an already-verified indicator. This indicator tells program C not to require the password (if program C is configured to accept an already-verified indicator).  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; the value specified by *conversation_ID* is invalid, or the address of a variable is invalid.  
  
## State Changes  
 The conversation can be in any state except RESET.  
  
 There is no state change.