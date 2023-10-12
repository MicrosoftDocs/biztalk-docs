---
description: "Learn more about: ConfigureLinkServiceEx"
title: "ConfigureLinkServiceEx1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ConfigureLinkServiceEx
The **ConfigureLinkServiceEx** function is used to add or modify a link service. This function must be exported from a link service configuration dynamic-link library (DLL)  supplied with each link service.  
  
## Syntax  
  
```  
  
          __declspec(dllexport) BOOL WINAPI ConfigureLinkServiceEx(   
LPSTRszComputerName,  
LPSTRszLinkServiceTitle,  
LPSTR* pvConfigInfo,  
LPDWORD dConfigInfoSize);  
```  
  
#### Parameters  
 *szComputerName*  
 This supplied parameter specifies the name of the computer that is to be configured.  
  
 *szLinkServiceTitle*  
 This supplied parameter specifies the title of the link service that is to be configured.  
  
 *pvConfigInfo*  
 This supplied and returned parameter points to a configuration buffer that is used to configure the link service.  
  
 *dConfigInfoSize*  
 This supplied parameter specifies the size of the *pvConfigInfo* configuration buffer.  
  
## Return Value  
 TRUE  
 The function executed successfully and network bindings need to be recalculated.  
  
 FALSE  
 One or more of the parameters passed to this function are invalid or network bindings do not need to be recalculated.
