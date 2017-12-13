---
title: "fStringCompare1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 84156cbd-821a-44ec-8cca-95a7f27388a9
caps.latest.revision: 3
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