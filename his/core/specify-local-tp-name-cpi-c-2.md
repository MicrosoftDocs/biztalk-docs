---
title: "Specify_Local_TP_Name (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b181b5f-5b1b-4a70-881f-4278fee35913
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Specify_Local_TP_Name (CPI-C)
The **Specify_Local_TP_Name** call (function name **cmsltp**) is issued by the program to indicate that it is able to accept incoming conversations that are directed to the name given.  
  
## Syntax  
  
```  
  
CM_ENTRY Specify_Local_TP_Name(   
  unsigned char FAR *TP_name,    
  CM_INT32 FAR *TP_name_length,    
  CM_INT32 FAR *return_code    
);  
```  
  
#### Parameters  
 *TP_name*  
 Supplied parameter. Specifies the starting address of the local transaction program (TP) name. The program name can contain up to 64 ASCII characters. The allowed characters are:  
  
- Uppercase and lowercase letters.  
  
- Numerals from 0 through 9.  
  
- Special characters, except the space.  
  
  You cannot use **Specify_Local_TP_Name** to specify the name of an SNA service TP.  
  
  Double-byte character sets, such as Kanji, are not supported.  
  
  *TP_name_length*  
  Supplied parameter. Specifies the length of the local program name. The range is from 1 through 64.  
  
  *return_code*  
  The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; one of the following occurred:  
  
- The *TP_name* supplied is invalid.  
  
- The value specified by *TP_name_length* is out of range (greater than 64 or less than 1).  
  
  CM_PRODUCT_SPECIFIC_ERROR  
  Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The call is not associated with a particular conversation, and no state restrictions apply.  
  
 There is no state change.  
  
## Remarks  
 A program can issue this call more than once to handle incoming conversations with more than one TP name. The program can discover the actual name on the incoming conversation by calling [Extract_TP_Name](../core/extract-tp-name-cpi-c-2.md).