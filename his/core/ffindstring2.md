---
title: "fFindString2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e7a8b5b-24d3-48b8-aab0-c5e18e3b9811
caps.latest.revision: 3
---
# fFindString
The **fFindString** function is used to determine if a string exists within a string buffer. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
          BOOL fFindString(   
LPSTRszStringBuffer,  
LPSTRszSearchString);  
```  
  
#### Parameters  
 *szStringBuffer*  
 This supplied parameter specifies the string buffer to search.  
  
 *szSearchString*  
 This supplied parameter specifies the string to search for.  
  
## Return Value  
 TRUE  
 The string was found.  
  
 FALSE  
 The string was not found.