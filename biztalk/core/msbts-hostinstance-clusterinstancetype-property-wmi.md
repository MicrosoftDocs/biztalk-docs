---
title: "MSBTS_HostInstance.ClusterInstanceType Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: add87697-1a91-4f10-b278-2f71283444c7
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstance.ClusterInstanceType Property (WMI)
This property tells whether the BizTalk Host Instance NT service is clustered.  
  
## Syntax  
  
```  
  
uint32ClusterInstanceType;  
```  
  
## Return Value  
 The return value can be one of the following:  
  
 0UnClusteredInstance  
  
 1 ClusteredInstance  
  
 2ClusteredVirtualInstance  
  
## Remarks  
 The default value for this parameter is 0.  
  
 This property is read only.  
  
 The syntax shown is language neutral.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.