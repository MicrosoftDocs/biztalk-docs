---
title: "Set_CPIC_Side_Information (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6bee0144-7ea3-4d8e-ab6c-6de83528b250
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Set_CPIC_Side_Information (CPI-C)
The **Set_CPIC_Side_Information** call (function name **xcmssi**) adds or replaces a side information entry in memory. A CPI-C side information entry associates a set of conversation characteristics with a symbolic definition name. This call overrides entries having the same symbolic destination name.  
  
## Syntax  
  
```  
  
CM_ENTRY Set_CPIC_Side_Information(   
  unsigned char FAR *key_lock,             
  SIDE_INFO FAR *side_info_entry,          
  CM_INT32 FAR *side_info_entry_length,    
  CM_INT32 FAR *return_code                
);  
```  
  
#### Parameters  
 *key_lock*  
 Supplied parameter. This parameter is ignored.  
  
 *side_info_entry*  
 Supplied parameter. Specifies the contents of a side information entry. The following table describes the *side_info_entry* structure, which defines the format of the side information entry.  
  
|Offset|Description|Type|Length|  
|------------|-----------------|----------|------------|  
|0|*sym_dest_name*|unsigned char|8 bytes|  
|8|*partner_LU_name*|unsigned char|17 bytes|  
|25|*reserved*|unsigned char|3 bytes|  
|28|*TP_name_type*|signed long int|32 bits|  
|32|*TP_name*|unsigned char|64 bytes|  
|96|*mode_name*|unsigned char|8 bytes|  
|104|*conversation_ security_type*|signed long int|32 bits|  
|108|*security_user_ID*|unsigned char|8 bytes|  
|116|*security_password*|unsigned char|8 bytes|  
  
 The allowed characters for *sym_dest_name* are the uppercase letters (A through Z) and the numerals from 0 through 9.  
  
 **Set_CPIC_Side_Information** is the only CPI-C call that lets you specify an SNA service transaction program (TP) as the partner program. The SNA convention for naming a service TP is up to four characters. The first character is a hexadecimal byte between 0x00 and 0x3F. The remaining characters are translated from ASCII to EBCDIC.  
  
 For the allowed characters for the other fields, see the description of the corresponding **Set_** call. For example, for the *mode_name* field, see the description of the [Set_Mode_Name](../core/set-mode-name-cpi-c-2.md) call.  
  
 Each field in the structure must be left-aligned. Pad fields on the right with spaces as necessary.  
  
 *side_info_entry_length*  
 Supplied parameter. Specifies the length of *side_info_entry*. It is always 124.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; one of the following occurred:  
  
- A value specified in the *side_info_entry* structure is invalid.  
  
- The left character of the *side_info_entry* contains a space.  
  
  CM_PRODUCT_SPECIFIC_ERROR  
  Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation can be in any state.  
  
 There is no state change.  
  
## Remarks  
 Invalid string parameters in the side information (for example, specifying a nonexistent partner logical unit (LU)) are not detected until [Allocate](../core/allocate-cpi-c-2.md) is issued. The error is returned on a call following **Allocate**.