---
title: "CheckForExistingLinkService1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d1f141c8-7252-4301-b636-0c4a4eeda224
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
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