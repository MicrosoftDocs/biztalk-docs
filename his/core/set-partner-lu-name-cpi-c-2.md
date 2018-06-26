---
title: "Set_Partner_LU_Name (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0eb8d60e-6c7b-4e4a-8a4e-036b3dec4e90
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Set_Partner_LU_Name (CPI-C)
The **Set_Partner_LU_Name** call (function name **cmspln**) is issued by the invoking program to specify the partner logical unit (LU) name. This call overrides the partner LU name derived from the side information when the [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) call was issued. This call cannot be issued after [Allocate](../core/allocate-cpi-c-2.md) has been issued. Issuing this call has no effect on the side information itself.  
  
## Syntax  
  
```  
  
CM_ENTRY Set_Partner_LU_Name(   
  unsigned char FAR *conversation_ID,    
    unsigned char FAR *partner_LU_name,    
  CM_INT32 FAR *partner_LU_name_length,    
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md).  
  
 *partner_LU_name*  
 Supplied parameter. Specifies the starting address of the partner LU name. The mode name can contain up to 17 ASCII characters. The allowed characters are:  
  
- Uppercase letters.  
  
- Numerals from 0 through 9.  
  
  The partner LU name can be either:  
  
- An alias consisting of one through eight characters.  
  
- A fully qualified network name consisting of from 2 through 17 characters. A period separates the network identifier (which can be from zero through eight characters) from the network LU name (which can be from one through eight characters). If the network identifier is zero characters long, the period is still required.  
  
  The partner LU name must match the name of a partner LU established during configuration.  
  
  *partner_LU_name_length*  
  Supplied parameter. Specifies the length of the partner LU name. The range is from 1 through 17.  
  
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
  
- The value specified by *partner_LU_name_length* is out of range (greater than 17 or less than 1).  
  
  CM_PRODUCT_SPECIFIC_ERROR  
  Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation must be in INITIALIZE state.  
  
 There is no state change.  
  
## Remarks  
 Specifying an invalid value for *partner_LU_name* is not detected until [Allocate](../core/allocate-cpi-c-2.md) is issued.