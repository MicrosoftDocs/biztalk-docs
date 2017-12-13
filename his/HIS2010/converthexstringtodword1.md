---
title: "ConvertHexStringToDWORD1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2769001-3b6e-4693-b825-0e7fef19b0ff
caps.latest.revision: 3
---
# ConvertHexStringToDWORD
The **ConvertHexStringToDWORD** function is used to convert a hexadecimal string to a DWORD value. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
          BOOL ConvertHexStringToDWORD(   
LPSTRszHexString,  
LPDWORDdHexValue);  
```  
  
#### Parameters  
 *szHexString*  
 This supplied parameter specifies the hexadecimal string to be converted.  
  
 *dHexValue*  
 This supplied and returned parameter contains the DWORD value of the hexadecimal string if the function was successful.  
  
## Return Value  
 TRUE  
 The function executed successfully and the hexadecimal string was converted.  
  
 FALSE  
 One or more of the parameters passed to this function are invalid or the function failed.  
  
## Remarks  
 This function scans until a nonhexadecimal character is encountered. The hexadecimal formats recognized are xnnnn, 0xnnnn, or nnnn.