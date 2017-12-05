---
title: "fRemoveRegistryValue1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c0df631-0932-482f-ac8f-ba69349a2a72
caps.latest.revision: 3
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