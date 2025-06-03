---
description: "Learn more about: Set_Return_Control (CPI-C)"
title: "Set_Return_Control (CPI-C)2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
---
# Set_Return_Control (CPI-C)
The **Set_Return_Control** call (function name **cmsrc**) is issued by the invoking program to specify when the local logical unit (LU), acting on the session request from the local programs [Allocate](../core/allocate-cpi-c-2.md) call, should return control to the local program.  
  
## Syntax  
  
```  
  
CM_ENTRY Set_Return_Control(   
  unsigned char FAR *conversation_ID,    
    CM_INT32 FAR *return_control,          
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md).  
  
 *return_control*  
 Supplied parameter. Specifies when the local LU, acting on the [Allocate](../core/allocate-cpi-c-2.md) call, should return control to the local program. The following are allowed values:  
  
 CM_IMMEDIATE  
 The LU allocates a contention-winner session, if one is immediately available, and returns control to the program.  
  
 CM_WHEN_SESSION_ALLOCATED  
 The LU does not return control to the program until it allocates a session or encounters errors. If a session is not available, the program waits for one. (If the session limit is zero, the LU returns control immediately.)  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_STATE_CHECK  
 Primary return code; the conversation is not in INITIALIZE state.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; the value specified by *conversation_ID* or *return_control* is invalid.  
  
 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation must be in INITIALIZE state.  
  
 There is no state change.  
  
## Remarks  
 This call overrides the default return control established by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md). By default, control is returned when the session is allocated. This call cannot be issued after the [Allocate](../core/allocate-cpi-c-2.md) call has been issued.  
  
 For further information about sessions, see [Writing CPI-C Applications](./writing-cpi-c-applications1.md).  
  
 If the LU is unable to allocate a session, the notification is returned on the **Allocate** call.
