---
title: "fQueryRegistryValue1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ddb003b-870a-43e0-813a-21b21ad4d397
caps.latest.revision: 3
---
# fQueryRegistryValue
The **fQueryRegistryValue** function is used to query a value from the registry. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
        BOOL fQueryRegistryValue(  
        HKEY *   
        hGlobalKey,  
LPSTRszRegistryKey,  
LPSTRszRegistryValue,  
LPSTRszRegistryData,  
LPDWORDdSize);  
```  
  
#### Parameters  
 *hGlobalKey*  
 This supplied parameter specifies the handle of the registry.  
  
 *szRegistryKey*  
 This supplied parameter specifies the registry key.  
  
 *szRegistryValue*  
 This supplied parameter specifies the registry value name.  
  
 *szRegistryData*  
 This supplied parameter specifies the registry value data.  
  
 *dSize*  
 This supplied parameter specifies the size of the registry data.  
  
## Return Value  
 TRUE  
 The function executed successfully and the function was able to connect to the registry.  
  
 FALSE  
 The function failed.