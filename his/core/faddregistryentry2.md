---
description: "Learn more about: fAddRegistryEntry"
title: "fAddRegistryEntry2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# fAddRegistryEntry
The **fAddRegistryEntry** function is used to add a new registry value to the registry. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
          BOOL fAddRegistryEntry(   
HKEY *hGlobalKey,  
char *szRegistryValue,  
char *szRegistryData,  
DWORDdType,  
DWORDdSize);  
```  
  
#### Parameters  
 *hGlobalKey*  
 This supplied parameter specifies the handle of the registry to modify.  
  
 *szRegistryValue*  
 This supplied parameter specifies the registry value name to add.  
  
 *szRegistryData*  
 This supplied parameter specifies the registry value data to add.  
  
 *dType*  
 This supplied parameter specifies the registry value type. This parameter is supplied unchanged to the Win32® **RegSetValueEx** function.  
  
 *dSize*  
 This supplied parameter specifies the size of the registry value data. This parameter is supplied unchanged to the Win32 **RegSetValueEx** function.  
  
## Return Value  
 TRUE  
 The function executed successfully and the registry entry was added.  
  
 FALSE  
 The function failed and the registry entry was not added.
