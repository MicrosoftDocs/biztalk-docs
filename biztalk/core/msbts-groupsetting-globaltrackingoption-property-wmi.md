---
title: "MSBTS_GroupSetting.GlobalTrackingOption Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f2bcaa2-346b-4e19-8a22-796d9994d40c
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_GroupSetting.GlobalTrackingOption Property (WMI)
Gets the level of tracking that the BizTalk server should perform.  
  
 The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
uint32 GlobalTrackingOption;  
```  
  
## Remarks  
 This property is read-write.  
  
 The following table contains the permissible values for this property:  
  
|Description|Value|  
|-----------------|-----------|  
|Disable Tracking|0|  
|Normal Tracking|1|  
  
 Note that the integer values must be used in code and script.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.