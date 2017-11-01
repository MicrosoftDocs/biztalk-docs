---
title: "GetCodePageDisplayStr2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b0fb5631-2c79-4cc2-bb2a-c87e18443fb3
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# GetCodePageDisplayStr
The SNA National Language Support (SNANLS) **GetCodePageDisplayStr** function copies the SNANLS code page display name identified by a key to a character string passed as a parameter.  
  
## Syntax  
  
```  
  
BOOL WINAPI GetCodePageDisplayStr(   
Int nKey  
WCHAR *szDisplayStr  
Int IDisplayStr  
);  
```  
  
#### Parameters  
 *nKey*  
 Supplied parameter. The numeric key to a code page. This value is an opaque index into an array containing the code pages supported by SNANLS. This value is normally the *CodePageKey* member of a CodePage structure returned from a previous call to **FindFirstCodePage** or **FindNextCodePage**.  
  
 *szDisplayStr*  
 Supplied and returned parameter. A pointer to a wide-character array where the SNANLS display name for the specific code page should be copied.  
  
 On a successful return, the memory location pointed to by this parameter will be filled with the SNANLS display name for the specific code page. The character string is null terminated.  
  
 On failure, no changes will be made to the memory pointed to by this parameter.  
  
 *IDisplayStr*  
 Represents the number of available characters in the szDisplaystr parameter.  
  
## Return Value  
 The **GetCodePageDisplayStr** function returns a value of **TRUE** on success. On failure, the returned value is **FALSE**.  
  
## Remarks  
 This function is supported by SNANLS on [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)].