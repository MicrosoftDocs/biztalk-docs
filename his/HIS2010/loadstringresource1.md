---
title: "LoadStringResource1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71461fc7-5fb0-466e-9a4e-62c35954db3c
caps.latest.revision: 3
---
# LoadStringResource
The **LoadStringResource** function is used to load a string from a string resource. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
          void LoadStringResource (   
DWORDdStringResource,  
LPSTRpszString);  
```  
  
#### Parameters  
 *dStringResource*  
 This supplied parameter specifies the resource ID of the string resource.  
  
 *pszString*  
 This supplied and returned parameter specifies the buffer to place the string in.  
  
## Return Value  
 None