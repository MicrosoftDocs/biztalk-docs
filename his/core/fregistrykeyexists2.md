---
description: "Learn more about: fRegistryKeyExists"
title: "fRegistryKeyExists2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
