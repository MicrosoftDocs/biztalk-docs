---
title: "DisplayHelpInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 187cb25f-39f9-480a-96ed-43bddb76c8f6
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
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