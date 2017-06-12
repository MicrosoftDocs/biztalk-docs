---
title: "MSBTS_HostSetting.MessagePublishMaximumDelay Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b853465-446d-4a44-bad4-a5652ef6a436
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.MessagePublishMaximumDelay Property (WMI)
The maximum Delay (in milliseconds) imposed for Message Publishing Throttling. Zero indicates that Message Publishing Throttling is disabled.  
  
## Syntax  
  
```  
  
uint32MessagePublishMaximumDelay;  
```  
  
## Remarks  
 The default value for this parameter is 1000000.  
  
 This property is read/write.  
  
 The syntax shown is language neutral.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.