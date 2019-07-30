---
title: "fDisconnectRegistry1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b1b50087-dde1-48bf-ad65-33a25af17311
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
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