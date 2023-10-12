---
description: "Learn more about: fStringCompare"
title: "fStringCompare2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# fStringCompare
The **fStringCompare** function is used to determine if string exists in another string. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
BOOL fStringCompare (  
  LPSTR lpszString1,  
  LPSTR lpszString2  
);  
```  
  
#### Parameters  
 *lpszString1*  
 This supplied parameter specifies the string to search for.  
  
 *lpszString2*  
 This supplied parameter specifies the string to compare.  
  
## Return Value  
 TRUE  
 The string was found.  
  
 FALSE  
 The string was not found.
