---
description: "Learn more about: Set_Processing_Mode (CPI-C)"
title: "Set_Processing_Mode (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 06f24196-7c68-442e-a932-a28ab1f7dc3d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Set_Processing_Mode (CPI-C)
The **Set_Processing_Mode** call (function name **cmspm**) specifies for the conversation whether subsequent calls will be returned when the operation they have requested is complete (blocking) or immediately after the operation is initiated (nonblocking).  
  
> [!NOTE]
>  A program is notified of the completion of nonblocking calls when it issues [Wait_For_Conversation](../core/wait-for-conversation-cpi-c-1.md) or through a Microsoft® Windows® message sent to a WndProc identified by the *hWnd* in the [Specify_Windows_Handle](../core/specify-windows-handle-cpi-c-2.md) call.  
  
## Syntax  
  
```  
  
CM_ENTRY Set_Processing_Mode(   
  unsigned char FAR *conversation_ID,    
  CM_INT32 FAR *receive_type,            
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 *receive_type*  
 Supplied parameter. Specifies whether subsequent calls on the conversation will be blocking or nonblocking. Possible values are:  
  
 CM_BLOCKING  
 Subsequent calls will return only when the operation is complete.  
  
 CM_NON_BLOCKING  
 Subsequent calls will return immediately after the operation has been initiated.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_STATE_CHECK  
 Primary return code; the previous incomplete operation on the conversation has not yet completed.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; the value specified by *conversation_ID* or *processing_mode* is invalid.  
  
 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation can be in any state except RESET.  
  
 There is no state change.
