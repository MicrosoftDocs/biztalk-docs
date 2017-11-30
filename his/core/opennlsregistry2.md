---
title: "OpenNlsRegistry2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63f02fdc-cdd4-4d88-9a95-71c33bf56513
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# OpenNlsRegistry
The SNA National Language Support (SNANLS) **OpenNlsRegistry** function opens a registry key on a local or remote computer pointing to the NLS Codepage registry entries.  
  
## Syntax  
  
```  
  
HKEY WINAPI OpenNlsRegistry(   
char *MachineName,  
HKEY hkey,  
LPSTR Path  
);  
```  
  
#### Parameters  
 *MachineName*  
 Supplied parameter. The name of the remote computer on which to open the registry. If this parameter is NULL, the registry on the local computer is opened.  
  
 *hKey*  
 Supplied parameter. The key to the registry to open. If this parameter is NULL, the **HKEY_LOCAL_MACHINE** key is used.  
  
 *Path*  
 Supplied parameter. The path to the key value in the registry hive to open. If this parameter is NULL, the following key is opened:  
  
 SYSTEM\CurrentControlSet\NLS\CodePage.  
  
## Return Value  
 The **OpenNlsRegistry** function returns a handle to the opened registry key on success, otherwise a NULL value is returned on failure.  
  
## Remarks  
 This function is primarily used by the Print Service in [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] to determine if what code pages are supported on a remote computer providing the print services function.  
  
 This function is supported by SNANLS in [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)].