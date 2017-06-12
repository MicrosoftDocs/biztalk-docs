---
title: "MSBTS_Host.GetClusterResourceGroupNames (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6872748-cd0a-487a-acbe-69ae7e1a9d34
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Host.GetClusterResourceGroupNames (WMI)
This method returns a string array that contains a list of available cluster resource groups.  
  
## Syntax  
  
```  
  
uint32 GetClusterResourceGroupNames(string[] ClusterResourceGroupNames);  
```  
  
#### Parameters  
 string[] ClusterResourceGroupNames  
 List of available cluster resource groups.  
  
## Property Value/Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.