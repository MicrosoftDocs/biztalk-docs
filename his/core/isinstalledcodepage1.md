---
description: "Learn more about: IsInstalledCodePage"
title: "IsInstalledCodePage1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fea9230d-34e6-45bf-830b-60dc8df27ee7
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# IsInstalledCodePage
The SNA National Language Support (SNANLS) **IsInstalledCodePage** function determines if a code page is installed on a local or remote computer.  
  
## Syntax  
  
```  
  
BOOL WINAPI IsInstalledCodePage(   
UINTCodePage,  
HKEYKeyHandle  
);  
```  
  
#### Parameters  
 *CodePage*  
 Supplied parameter. The NLS code page.  
  
 *KeyHandle*  
 Supplied parameter. The registry key returned from a call to the **OpenNlsRegistry** function.  
  
## Return Value  
 The **IsInstalledCodePage** function returns non-zero if a code page is installed, otherwise a zero value is returned on failure.  
  
## Remarks  
 This function is primarily used by the Print Service in Host Integration Server to determine if what code pages are supported on a remote computer providing the print services function.  
  
 This function is supported by SNANLS on Host Integration Server.
