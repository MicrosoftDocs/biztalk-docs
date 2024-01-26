---
description: "Learn more about: DisplayHelpInfo"
title: "DisplayHelpInfo2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# DisplayHelpInfo
The **DisplayHelpInfo** function is used to generate help information used by the command-line interface to a link service dynamic-link library (DLL). This function must be exported from a link service configuration DLL supplied with each link service.  
  
## Syntax  
  
```  
  
          __declspec(dllexport) BOOL WINAPI DisplayHelpInfo(   
LPSTR*szHelpInfoBuffer);  
```  
  
#### Parameters  
 *szHelpInfoBuffer*  
 This supplied and returned parameter points to a buffer that on successful return contains help information that can be used to configure the link service.  
  
## Return Value  
 TRUE  
 The function executed successfully.  
  
 FALSE  
 The parameter passed to this function is invalid or the function failed.
