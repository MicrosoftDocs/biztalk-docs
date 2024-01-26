---
description: "Learn more about: fFindAndReplaceString"
title: "fFindAndReplaceString2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# fFindAndReplaceString
The **fFindAndReplaceString** function is used to find and replace a substring within a string. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
          BOOL fFindAndReplaceString(   
LPSTRszStringBuffer,  
LPSTRszSearchString,  
LPSTRszReplaceString);  
```  
  
#### Parameters  
 *szStringBuffer*  
 This supplied parameter specifies the string buffer to search.  
  
 *szSearchString*  
 This supplied parameter specifies the string to search for.  
  
 *szReplaceString*  
 This supplied parameter specifies the replacement string.  
  
## Return Value  
 TRUE  
 The string was found.  
  
 FALSE  
 The string was not found.
