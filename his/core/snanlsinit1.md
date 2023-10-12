---
description: "Learn more about: SnaNlsInit"
title: "SnaNlsInit1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SnaNlsInit
The **SnaNlsInit** function is called to determine if the code page needed is supported by code page translations using SNA National Language Support (SNANLS). This enables an application to determine if the necessary NLS language files containing code page translation tables are installed on the local system.  
  
## Syntax  
  
```  
  
int WINAPI SnaNlsInit(   
UINTCodePage  
);  
```  
  
#### Parameters  
 *CodePage*  
 Supplied parameter. The number of the NLS code page for which support is requested. The *CodePage* parameter corresponds with the registry settings on Microsoft Windows located under the **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage** subkey.  
  
## Return Value  
 The **SnaNlsInit** function returns non-zero if code page translations are supported; otherwise 0 is returned.  
  
## Remarks  
 If CP_ACP (the current ANSI code page) is passed as the *CodePage* parameter, this functions returns non-zero.  
  
 This function is supported by SNANLS on Microsoft® Host Integration Server.
