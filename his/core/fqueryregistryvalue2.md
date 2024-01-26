---
description: "Learn more about: fQueryRegistryValue"
title: "fQueryRegistryValue2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
