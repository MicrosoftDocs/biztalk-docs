---
description: "Learn more about: Delete_CPIC_Side_Information (CPI-C)"
title: "Delete_CPIC_Side_Information (CPI-C)2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Delete_CPIC_Side_Information (CPI-C)
The **Delete_CPIC_Side_Information** call (function name **xcmdsi**) deletes an entry from the side information table in memory. The side information entry is identified through the symbolic destination name.  
  
## Syntax  
  
```  
  
CM_ENTRY Delete_CPIC_Side_Information(   
  unsigned char FAR *key_lock,         
    unsigned char FAR *sym_dest_name,    
    CM_INT32 FAR *return_code            
);  
```  
  
#### Parameters  
 *key_lock*  
 Supplied parameter. This parameter is ignored.  
  
 *sym_dest_name*  
 Supplied parameter. Specifies the symbolic destination name of the entry to be deleted.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; the *sym_dest_name* parameter specified a nonexistent side information entry.  
  
 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The call is not associated with a conversation and can be in any state.  
  
 There is no state change.  
  
## Remarks  
 The side information entry is removed immediately from the side information table in memory.  
  
 While this call is being executed, any calls issued by other CPI-C applications that set or extract side information are suspended. These calls include the following:  
  
-   [Set_CPIC_Side_Information](../core/set-cpic-side-information-cpi-c-2.md)  
  
-   [Extract_CPIC_Side_Information](../core/extract-cpic-side-information-cpi-c-1.md)  
  
-   [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md)
