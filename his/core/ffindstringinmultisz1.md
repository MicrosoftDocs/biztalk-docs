---
description: "Learn more about: fFindStringInMultiSZ"
title: "fFindStringInMultiSZ1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# fFindStringInMultiSZ
The **fFindStringInMultiSZ** function is used to determine if string exists in a REG_MULTI_SZ string list and return entire string. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
        BOOL fFindString(  
        LPSTR  
        szStringBuffer,  
LPSTRszSearchString,  
LPSTRszFoundString);  
```  
  
#### Parameters  
 *szStringBuffer*  
 This supplied parameter specifies the string buffer to search.  
  
 *szSearchString*  
 This supplied parameter specifies the string to search for.  
  
 *szFoundString*  
 This supplied and returned parameter specifies the full string containing string if successful.  
  
## Return Value  
 TRUE  
 The string was found and returned.  
  
 FALSE  
 The string was not found.
