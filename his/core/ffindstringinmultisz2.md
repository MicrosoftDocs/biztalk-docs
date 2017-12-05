---
title: "fFindStringInMultiSZ2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80a2dc28-df7e-4190-a218-f39e7af80ac5
caps.latest.revision: 3
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