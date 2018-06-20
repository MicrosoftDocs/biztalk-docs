---
title: "Extract_CPIC_Side_Information (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc73acb7-0a0e-48a9-9f31-3993c8f1b407
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Extract_CPIC_Side_Information (CPI-C)
The **Extract_CPIC_Side_Information** call (function name **xcmesi**) returns the side information for an entry number or symbolic destination name.  
  
## Syntax  
  
```  
  
CM_ENTRY Extract_CPIC_Side_Information(   
  CM_INT32 FAR *entry_number,          
  unsigned char FAR *sym_dest_name,    
  SIDE_INFO FAR *side_info_entry,      
  CM_INT32 FAR *side_info_entry_length,    
    CM_INT32 FAR *return_code            
);  
```  
  
#### Parameters  
 *entry_number*  
 Supplied parameter. Specifies the number (index) of the side information entry to be returned. The first entry is 1.  
  
 The program can look up the side information entry by the symbolic destination name instead. To accomplish this, set the entry number to zero.  
  
 *sym_dest_name*  
 Supplied parameter. Specifies the symbolic destination name to search for.  
  
 If *entry_number* is set to a number greater than zero, this parameter is ignored.  
  
 *side_info_entry*  
 Returned parameter. Specifies the side information entry. For a detailed explanation of the side information entry, see [Set_CPIC_Side_Information](../core/set-cpic-side-information-cpi-c-2.md).  
  
 Each field in the side information structure is left-aligned and padded with spaces on the right as necessary.  
  
 *side_info_entry_length*  
 Supplied parameter. Always 124.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; one of the following occurred:  
  
- The *entry_number* specified a number larger than the maximum number of entries in the side information table or a number that is less than zero.  
  
- The *sym_dest_name* parameter is invalid and *entry_number* is set to zero.  
  
- The *side_info_entry_length* parameter is not set to 124.  
  
  CM_PRODUCT_SPECIFIC_ERROR  
  Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 This call is not associated with a conversation and can be in any state.  
  
 There is no state change.  
  
## Remarks  
 The security password is never returned. If the security user identifier in the side information is not set, the security user identifier field is returned as all spaces.