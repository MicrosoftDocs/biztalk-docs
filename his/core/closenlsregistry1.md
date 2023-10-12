---
description: "Learn more about: CloseNlsRegistry"
title: "CloseNlsRegistry1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# CloseNlsRegistry
The SNA National Language Support (SNANLS) **CloseNlsRegistry** function closes an open registry key on a local or remote computer.  
  
## Syntax  
  
```  
  
BOOL WINAPI CloseNlsRegistry(  
HKEY KeyHandle  
);  
```  
  
#### Parameters  
 `KeyHandle`  
 Supplied parameter. The handle to a key in the registry opened using **OpenNlsRegistry**.  
  
## Return Value  
 The **CloseNlsRegistry** function returns zero on success, otherwise a non-zero value is returned on failure.  
  
## Remarks  
 The *KeyHandle* parameter passed to this function is the handle returned from a previous call to the **OpenNlsRegistry** function. This function is primarily used by the Print service in Host Integration Server to determine what code pages are supported on a remote computer providing the print services function.  
  
 SNANLS supports this function on Microsoft Host Integration Server.
