---
title: "Set_Mode_Name (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33b257c7-511f-4dc4-89ad-598121f8eb36
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Set_Mode_Name (CPI-C)
The **Set_Mode_Name** call (function name **cmsmn**) is issued by the invoking program to specify the mode name for a conversation. This call overrides the system-defined mode name derived from the side information when the [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) call was issued. This call cannot be issued after [Allocate](../core/allocate-cpi-c-2.md)has been issued. Issuing this call has no effect on the side information itself.  
  
## Syntax  
  
```  
  
CM_ENTRY Set_Mode_Name(   
  unsigned char FAR *conversation_ID,    
  unsigned char FAR *mode_name,      
  CM_INT32 FAR *mode_name_length,    
  CM_INT32 FAR *return_code          
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md).  
  
 *mode_name*  
 Supplied parameter. Specifies the starting address of the mode name (the name of a set of networking characteristics defined during configuration). The mode name can contain up to eight ASCII characters. The allowed characters are:  
  
- Uppercase letters.  
  
- Numerals from 0 through 9.  
  
  The value of *mode_name* must match the name of a mode associated with the partner logical unit (LU) during configuration. The mode name cannot be SNASVCMG or CPSVCMG.  
  
  *mode_name_length*  
  Supplied parameter. Specifies the length of the mode name. The range is from 0 through 8 bytes.  
  
  If *mode_name_length* is set to zero, **Set_Mode_Name** is ignored.  
  
  *return_code*  
  The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_STATE_CHECK  
 Primary return code; the conversation is not in INITIALIZE state.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; one of the following occurred:  
  
- The value specified by *conversation_ID* is invalid.  
  
- The value specified by *mode_name_length* is out of range (greater than 8 or less than 0).  
  
  CM_PRODUCT_SPECIFIC_ERROR  
  Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation must be in INITIALIZE state.  
  
 There is no state change.  
  
## Remarks  
 Specifying an invalid value for *mode_name* is not detected until [Allocate](../core/allocate-cpi-c-2.md) is issued.