---
title: "fRegistryKeyExists1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb06ed15-b955-42e8-bc55-7dae0f446357
caps.latest.revision: 3
---
# fRegistryKeyExists
The **fRegistryKeyExists** function is used to determine if a registry key already exists in the registry. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
            BOOL fRegistryKeyExists (   
  HKEY *hGlobalKey,  
  LPSTRszRegistryKey   
);  
```  
  
#### Parameters  
 *hGlobalKey*  
 This supplied parameter specifies the handle of the registry.  
  
 *szRegistryKey*  
 This supplied parameter specifies the registry key.  
  
## Return Value  
 TRUE  
 The registry key exists.  
  
 FALSE  
 The function failed or the registry key does not exist.