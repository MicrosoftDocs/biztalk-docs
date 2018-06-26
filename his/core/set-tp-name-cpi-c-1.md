---
title: "Set_TP_Name (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dcde03ca-6c97-4105-b204-c9a07afd4d46
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Set_TP_Name (CPI-C)
The **Set_TP_Name** call (function name **cmstpn**) is issued by the invoking program to specify the partner (invokable) program name. This call overrides the partner program name derived from the side information when the [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) call was issued. This call cannot be issued after the [Allocate](../core/allocate-cpi-c-2.md) call has been issued. Issuing this call has no effect on the side information itself.  
  
## Syntax  
  
```  
  
CM_ENTRY Set_TP_Name(   
  unsigned char FAR *conversation_ID,    
    unsigned char FAR *TP_name,            
    CM_INT32 FAR *TP_name_length,          
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md).  
  
 *TP_name*  
 Supplied parameter. Specifies the starting address of the partner program name. The program name can contain up to 64 ASCII characters. The allowed characters are:  
  
- Uppercase and lowercase letters.  
  
- Numerals from 0 through 9.  
  
- Special characters, except the space.  
  
  You cannot use **Set_TP_Name** to specify the name of an SNA service transaction program (TP). You can, however, use [Set_CPIC_Side_Information](../core/set-cpic-side-information-cpi-c-2.md) to do this.  
  
  Double-byte character sets, such as Kanji, are not supported.  
  
  *TP_name_length*  
  Supplied parameter. Specifies the length of the partner program name. The range is from 1 through 64.  
  
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
  
- The value specified by *TP_name_length* is out of range (greater than 64 or less than 1).  
  
- The address of a variable is invalid.  
  
  CM_PRODUCT_SPECIFIC_ERROR  
  Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation must be in INITIALIZE state.  
  
 There is no state change.