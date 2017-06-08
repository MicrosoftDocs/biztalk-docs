---
title: "MSBTS_GroupSetting.ConfigurationCacheRefreshInterval Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e51e7730-3fa6-4d9c-b268-d54372fda962
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_GroupSetting.ConfigurationCacheRefreshInterval Property (WMI)
Gets or sets a value indicating how often BizTalk Server refreshes the cache of the messaging configuration objects, in seconds.  
  
 The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
uint32 ConfigurationCacheRefreshInterval = 60;  
```  
  
## Remarks  
 This property is read-write.  
  
 Maximum value for this property is 43200 and minimum value is 1.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.