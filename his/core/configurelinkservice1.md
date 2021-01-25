---
description: "Learn more about: ConfigureLinkService"
title: "ConfigureLinkService1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 800a35d2-aa92-4878-93d8-90119ff2073d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# ConfigureLinkService
The **ConfigureLinkService** function is used to add or modify a link service. This function must be exported from a link service configuration dynamic-link library (DLL)  supplied with each link service.  
  
## Syntax  
  
```  
  
          __declspec(dllexport) BOOL WINAPI ConfigureLinkService(   
LPSTR szComputerName,  
LPSTRszLinkServiceTitle);  
```  
  
#### Parameters  
 *szComputerName*  
 This supplied parameter specifies the name of the computer that is to be configured.  
  
 *szLinkServiceTitle*  
 This supplied parameter specifies the title of the link service that is to be configured.  
  
## Return Value  
 TRUE  
 The function executed successfully and network bindings need to be recalculated.  
  
 FALSE  
 One or more of the parameters passed to this function are invalid or network bindings do not need to be recalculated.
