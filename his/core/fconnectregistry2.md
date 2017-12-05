---
title: "fConnectRegistry2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c10e42b5-d03e-4c58-a767-36ae93d72514
caps.latest.revision: 3
---
# fConnectRegistry
The **fConnectRegistry** function is used to connect to a remote computer's registry and return a handle to the remote registry. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
          BOOL fConnectRegistry(   
HKEY *hGlobalKey,  
LPSTR *szComputerName);  
```  
  
#### Parameters  
 *hGlobalKey*  
 This supplied parameter specifies the handle of the registry to connect to.  
  
 *szComputerName*  
 This supplied parameter specifies the computer name to connect to.  
  
## Return Value  
 TRUE  
 The function executed successfully and the function was able to connect to the registry.  
  
 FALSE  
 The function failed.