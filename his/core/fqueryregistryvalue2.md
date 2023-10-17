---
description: "Learn more about: fQueryRegistryValue"
title: "fQueryRegistryValue2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04338b82-3c6d-45a9-88f4-ac3dc2c02a05
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
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
