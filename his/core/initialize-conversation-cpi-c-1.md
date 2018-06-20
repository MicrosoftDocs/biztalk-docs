---
title: "Initialize_Conversation (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b51a11a-2456-4778-8a5c-9b0e78bb0ecf
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Initialize_Conversation (CPI-C)
The **Initialize_Conversation** call (function name **cminit**) is issued by the invoking program to obtain an 8-byte conversation identifier and to set the initial values for the conversations characteristics.  
  
## Syntax  
  
```  
  
CM_ENTRY Initialize_Conversation(   
  unsigned char FAR *conversation_ID,    
  unsigned char FAR *sym_dest_name,    
  CM_INT32 FAR *return_code            
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Returned parameter. Specifies the identifier for the conversation. It is used by subsequent CPI-C calls.  
  
 *sym_dest_name*  
 Supplied parameter. Specifies the symbolic destination name—the name associated with a side information entry loaded from the configuration file or defined by [Set_CPIC_Side_Information](../core/set-cpic-side-information-cpi-c-2.md) calls.  
  
 This parameter is an 8-byte ASCII character string. The allowed characters are as follows:  
  
- Uppercase letters  
  
- Numerals from 0 through 9  
  
  This parameter can also be set to eight spaces. In this case, the invoking program must issue the following calls before issuing [Allocate](../core/allocate-cpi-c-2.md):  
  
- [Set_Mode_Name](../core/set-mode-name-cpi-c-2.md)  
  
- [Set_Partner_LU_Name](../core/set-partner-lu-name-cpi-c-2.md)  
  
- [Set_TP_Name](../core/set-tp-name-cpi-c-1.md)  
  
  *return_code*  
  The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; the value specified by *sym_dest_name* does not match a symbolic destination name in the side information table and is not a space.  
  
 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation is in RESET state.  
  
 If the *return_code* is CM_OK, the conversation changes to INITIALIZE state. For other return codes, the conversation state remains unchanged.  
  
## Remarks  
 The initial values are CPI-C defaults or are derived from side information associated with the symbolic destination name. For more information about initial values and side information, see [Initial Conversation Characteristics](./initial-conversation-characteristics1.md) and [Side Information for CPI-C Programs](./side-information-for-cpi-c-programs1.md).  
  
 Initial values can be changed by the **Set_** calls.  
  
 If the side information contains an invalid value or a **Set_** call sets a conversation characteristic to an invalid value, the error is returned on the **Allocate** call.  
  
 If a CPI-C application attempts to invoke more than one concurrent conversation, only a single local APPC logical unit (LU) is used by all conversations. This prevents concurrent conversations across two or more dependent LU 6.2 LUs, causing subsequent Initialize_Conversation (CMALLC) calls to wait for the first conversation to be deallocated.  
  
 If the CPI-C application needs to invoke more than one concurrent conversation, independent LU 6.2 must be used between Host Integration Server and the remote system.  
  
 Upon successful execution of this call, CPI-C generates a conversation identifier. This identifier is a required parameter for all other CPI-C calls issued for this conversation by the invoking program.  
  
 Under normal circumstances, a CPI-C application cannot invoke two concurrent conversations using two different local APPC LUs. A registry key is available that when set forces CPI-C to issue a new TP_STARTED verb on every Initialize_Conversation (cminit) call. This is necessary to force APPC resource location for each call. The registry key that must be defined to force this behavior is the following:  
  
 \HKLM\CurrentControlSet\Services\SnaBase\Parameters\Client\GETNEWTPID