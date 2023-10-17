---
description: "Learn more about: RemoveAllLinkServices"
title: "RemoveAllLinkServices1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b69bec4b-1b98-4d94-a79f-41d04e175e2f
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# RemoveAllLinkServices
The **RemoveAllLinkServices** function is used to remove all link services from a machine. This function must be exported from a link service configuration dynamic-link library (DLL)  supplied with each link service.  
  
## Syntax  
  
```  
  
          __declspec(dllexport) BOOL WINAPI RemoveAllLinkServices(   
LPSTRszComputerName);  
```  
  
#### Parameters  
 *szComputerName*  
 This supplied parameter specifies the name of the computer that is to have all link services removed.  
  
## Return Value  
 TRUE  
 The function executed successfully and network bindings need to be recalculated.  
  
 FALSE  
 The parameter passed to this function is invalid or network bindings do not need to be recalculated.
