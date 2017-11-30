---
title: "fFindAndReplaceString2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e556c38-8a32-458f-823d-4fb12e2a05a4
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
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