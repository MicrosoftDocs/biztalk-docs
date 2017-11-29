---
title: "CommandLineAdd2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71fa9f3e-1e76-4e5e-8d01-df324c09793e
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# CommandLineAdd
The **CommandLineAdd** function is used to add a new link service using a command-line interface. This function must be exported from a link service configuration dynamic-link library (DLL)  supplied with each link service.  
  
## Syntax  
  
```  
  
__declspec(dllexport) BOOL WINAPI CommandLineAdd(  LPSTRszCommandLine,  
  LPSTR *szConfigInfo,  
  LPDWORD dConfigInfoSize);  
```  
  
#### Parameters  
 *szCommandLine*  
 This supplied parameter specifies the command line containing information on the computer and link service to be configured.  
  
 *szConfigInfo*  
 This supplied and returned parameter points to a configuration buffer that is used to configure the link service.  
  
 *dConfigInfoSize*  
 This supplied parameter specifies the size of the sz*ConfigInfo* configuration buffer .  
  
## Return Value  
 TRUE  
 The function executed successfully.  
  
 FALSE  
 One or more of the parameters passed to this function are invalid or the function failed.