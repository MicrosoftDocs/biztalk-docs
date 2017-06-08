---
title: "MSBTS_HostSetting.InflightMessageThreshold Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bace1a98-8c17-4613-bc42-1712e02fbf3d
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.InflightMessageThreshold Property (WMI)
This property represents the maximum number of in-memory in-flight messages allowed before throttling Message Delivery begins.  
  
## Syntax  
  
```  
  
uint32InflightMessageThreshold;  
```  
  
## Remarks  
 The default value for this parameter is 1000.  
  
 This property is read/write.  
  
 The syntax shown is language neutral.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.