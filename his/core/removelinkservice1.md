---
title: "RemoveLinkService1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0ef9ff9-29a0-456a-87be-6844ee2ca7f6
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# RemoveLinkService
The **RemoveLinkService** function is used to remove a link service. This function must be exported from a link service configuration dynamic-link library (DLL)  supplied with each link service.  
  
## Syntax  
  
```  
  
          __declspec(dllexport) BOOL WINAPI RemoveLinkService(   
LPSTRszComputerName,  
LPSTRszLinkServiceTitle);  
```  
  
#### Parameters  
 *szComputerName*  
 This supplied parameter specifies the name of the computer that is to have the link service removed.  
  
 *szLinkServiceTitle*  
 This supplied parameter specifies the title of the link service that is to be removed.  
  
## Return Value  
 TRUE  
 The function executed successfully and network bindings need to be recalculated.  
  
 FALSE  
 One or more of the parameters passed to this function are invalid or network bindings do not need to be recalculated.  
  
 This section contains:  
  
-   [Utility Functions Used by a Link Service Configuration DLL](../core/utility-functions-used-by-a-link-service-configuration-dll1.md)