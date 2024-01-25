---
description: "Learn more about: fRemoveRegistryEntry"
title: "fRemoveRegistryEntry1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# fRemoveRegistryEntry
The **fRemoveRegistryEntry** function is used to remove a registry key from the registry. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
            BOOL  
            fRemoveRegistryEntry  
            (  
            HKEY *  
            hGlobalKey,  
    char *szRegistryKey   
);  
```  
  
#### Parameters  
 *hGlobalKey*  
 This supplied parameter specifies the handle of the registry.  
  
 *szRegistryKey*  
 This supplied parameter specifies the registry key.  
  
## Return Value  
 TRUE  
 The function was successful and the registry key was removed.  
  
 FALSE  
 The function failed or the registry key could not be removed.
