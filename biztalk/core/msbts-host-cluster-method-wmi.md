---
title: "MSBTS_Host.Cluster Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: caa455d2-33f8-4383-ab5b-7025d12dd662
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Host.Cluster Method (WMI)
This method clusters all BizTalk Host Instances on the given BizTalk Host.  
  
## Syntax  
  
```  
  
uint32 Cluster(string ClusterResourceGroupName);  
```  
  
#### Parameters  
 string ClusterResourceGroupName  
 The cluster resource group name to be used.  
  
## Property Value/Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.