---
title: "fRemoveRegistryEntry2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e44a37b-12e6-440d-9213-d473d0445d59
caps.latest.revision: 3
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