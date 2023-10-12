---
description: "Learn more about: fRemoveRegistryValue"
title: "fRemoveRegistryValue2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# fRemoveRegistryValue
The **fRemoveRegistryValue** function is used to remove a registry value from the registry. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
            BOOL fRemoveRegistryValue (  
            HKEY *   
            hGlobalKey,  
    char *szRegistryKey,   
    char *szRegistryValue   
);  
```  
  
#### Parameters  
 *hGlobalKey*  
 This supplied parameter specifies the handle of the registry.  
  
 *szRegistryKey*  
 This supplied parameter specifies the registry key.  
  
 *szRegistryValue*  
 This supplied parameter specifies the registry value to remove.  
  
## Return Value  
 TRUE  
 The function was successful and the registry value was removed.  
  
 FALSE  
 The function failed or the registry value could not be removed.
