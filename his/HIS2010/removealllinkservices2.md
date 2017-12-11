---
title: "RemoveAllLinkServices2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 232c85cc-9fbf-4ef5-b8b5-1987a5237071
caps.latest.revision: 3
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