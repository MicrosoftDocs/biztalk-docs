---
description: "Learn more about: fDisconnectRegistry"
title: "fDisconnectRegistry1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# fDisconnectRegistry
The **fDisconnectRegistry** function is used to disconnect from a remote computer's registry. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
          BOOL fDisconnectRegistry(   
HKEY *hGlobalKey);  
```  
  
#### Parameters  
 *hGlobalKey*  
 This supplied parameter specifies the handle of the registry from which to disconnect.  
  
## Return Value  
 TRUE  
 The function executed successfully and the function was able to disconnect from the registry.  
  
 FALSE  
 The function failed.
