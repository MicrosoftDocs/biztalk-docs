---
title: "fStringCompare2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57de188f-62a4-4543-8c44-ae7cac5a2c07
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
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