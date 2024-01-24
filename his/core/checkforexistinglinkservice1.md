---
description: "Learn more about: CheckForExistingLinkService"
title: "CheckForExistingLinkService1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# CheckForExistingLinkService
The **CheckForExistingLinkService** function is used to check to see if a link service of this type exists with this title. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
          BOOL bCreateService(   
HKEY *hGlobalKey,  
LPSTRszLinkRegistryRoot,  
LPSTRszTitle);  
```  
  
#### Parameters  
 *hGlobalKey*  
 This supplied parameter specifies the handle of the registry to search.  
  
 *szLinkRegistryRoot*  
 This supplied parameter specifies the registry root for this type of link service to search for.  
  
 *szTitle*  
 This supplied parameter specifies the title of the link service to search for.  
  
## Return Value  
 TRUE  
 The link service was located.  
  
 FALSE  
 One or more of the parameters passed to this function are invalid or the link service was not located.
