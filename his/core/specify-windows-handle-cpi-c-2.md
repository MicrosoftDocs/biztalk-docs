---
title: "Specify_Windows_Handle (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 614e5541-2276-4055-89f4-d13721bf2a7a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Specify_Windows_Handle (CPI-C)
The **Specify_Windows_Handle** call (function name **xchwnd**) sets the Microsoft® Windows® handle to which a message is sent on completion of an operation in nonblocking mode.  
  
## Syntax  
  
```  
  
CM_ENTRY Specify_Windows_Handle(   
  HWND hwndNotify,             
  CM_INT32 FAR *return_code    
);  
```  
  
#### Parameters  
 *hwndNotify*  
 Supplied parameter. Specifies the Windows handle to be notified when the outstanding operation completes.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 The Windows handle is invalid.  
  
 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The state change is dependent on the operation that completed and its return code.  
  
## Remarks  
 An application can set the processing mode by calling [Set_Processing_Mode](../core/set-processing-mode-cpi-c-2.md). If the Windows handle is set to NULL, or this call is never issued, the application must call [Wait_For_Conversation](../core/wait-for-conversation-cpi-c-1.md) to be notified when the outstanding operation completes.  
  
 When an asynchronous operation is complete, the applications window *hwndNotify* receives the message returned by **RegisterWindowMessage** with "WinAsyncCPIC" as the input string. The *wParam* value contains the *conversation_return_code* from the operation that is completing. Its values will depend on which operation was originally issued. The *lParam* argument contains the CM_PTR to the *conversation_ID* specified in the original function call.