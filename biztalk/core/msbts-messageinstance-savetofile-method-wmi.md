---
title: "MSBTS_MessageInstance.SaveToFile Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7758e76b-a0e6-4830-9974-b82365f03265
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_MessageInstance.SaveToFile Method (WMI)
Enables an administrator to save message context and parts into multiple output files.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
uint32 SaveToFile(string OutputFolderFullPath);  
```  
  
#### Parameters  
 *OutputFolderFullPath*  
 The full name of the output path in which to save the message context and parts.  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.