---
title: "Convert_Incoming (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f5dfef04-b504-49ee-9cb4-023a45055b13
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Convert_Incoming (CPI-C)
The **Convert_Incoming** call (function name **cmcnvi**) converts a string of EBCDIC characters into ASCII. Note that the return conversion can be performed using **Convert_Outgoing**.  
  
## Syntax  
  
```  
  
CM_ENTRY Convert_Incoming(   
  unsigned char FAR *string,    
  CM_INT32 FAR *string_length,  
  CM_INT32 FAR *return_code   
);  
```  
  
#### Parameters  
 *string*  
 Supplied parameter. Specifies the EBCDIC string to be converted. The string may contain any of the following characters:  
  
- Uppercase A–Z  
  
- Lowercase a–z  
  
- Numbers 0–9  
  
- The period (.)  
  
- Space characters  
  
- The special characters \< > + - ( ) & * ; : , '  ? / _= ".  
  
  *string_length* characters of this string will be replaced by ASCII equivalents.  
  
  *string_length*  
  Supplied parameter. Specifies the number of characters to be converted (1–32767).  
  
  *return_code*  
  The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully, and the *string* parameter now contains the converted ASCII string.  
  
 CM_OPERATION_NOT_ACCEPTED  
 Primary return code; the *string_length* parameter specified an invalid value.  
  
 CM_PRODUCT_SPECIFIC_ERROR  
 Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation can be in any state.  
  
 There is no state change.  
  
## Remarks  
 When data is being received in buffer format in a basic conversation, the data buffer may contain multiple logical records, each consisting of a 2-byte length field (NN) followed by the data. The application must extract and convert each data string separately (excluding the length field value). The applications must not attempt to convert the whole buffer in one operation, because this will make the length field values invalid.