---
title: "Wait_For_Conversation (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51a4c1f4-36de-40a1-bb96-eef9bfde3414
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Wait_For_Conversation (CPI-C)
The **Wait_For_Conversation** call (function name **cmwait**) waits for an operation to complete that has been initiated when the *processing_mode* conversation characteristic was set to CM_NON_BLOCKING and CM_OPERATION_INCOMPLETE was returned in the *return_code* parameter.  
  
## Syntax  
  
```  
  
CM_ENTRY Wait_For_Conversation(   
  unsigned char FAR *conversation_ID,    
  CM_INT32 FAR *conversation_return_code,    
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Returned parameter. Specifies the identifier for the conversation on which the operation completed. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 *conversation_return_code*  
 Returned parameter. Specifies the *return_code* from the operation that is completing. Its values will depend on which operation was originally issued.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_SYSTEM_EVENT  
 Primary return code; the wait completed not because the operation completed but because some system event occurred.  
  
 CM_PROGRAM_STATE_CHECK  
 Primary return code; the program has no incomplete operation outstanding.  
  
 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error has occurred and has been logged in the products error log.  
  
## State Changes  
 The state change is dependent on the operation that completed and its return code.  
  
## Remarks  
 The program must have an incomplete operation outstanding on some conversation.  
  
## See Also  
 [Set_Processing_Mode (CPI-C)](../core/set-processing-mode-cpi-c-2.md)   
 [Specify_Windows_Handle (CPI-C)](../core/specify-windows-handle-cpi-c-2.md)