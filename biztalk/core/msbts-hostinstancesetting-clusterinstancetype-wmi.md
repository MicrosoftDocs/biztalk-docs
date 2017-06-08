---
title: "MSBTS_HostInstanceSetting.ClusterInstanceType (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e8c40a5-9c35-4159-bd5f-c8608e63ed03
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstanceSetting.ClusterInstanceType (WMI)
This property tells whether the BizTalk Host Instance NT service is clustered.  
  
## Syntax  
  
```  
  
uint32ClusterInstanceType;  
```  
  
## Return values  
 Possible values are:  
  
 0UnClusteredInstance  
  
 1ClusteredInstance  
  
 2ClusteredVirtualInstance  
  
## Remarks  
 The default value for this parameter is 0.  
  
 This property is read only.  
  
 The syntax shown is language neutral.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.