---
title: "MSBTS_HostSetting.SubscriptionPauseAt Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: caa006f1-e5ac-40b9-9558-c4eb2f87ea29
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.SubscriptionPauseAt Property (WMI)
Specifies the number of messages a subscription must have waiting to be consumed before message delivery to that subscription instance is paused.  
  
 The syntax shown is language neutral.  
  
## Syntax  
  
```  
uint32  SubscriptionPauseAt;  
```  
  
## Remarks  
 This property is read/write.  
  
 The default value of this property is 0.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.