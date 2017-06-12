---
title: "MSBTS_HostSetting.SubscriptionResumeAt Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ca4c24c3-4a9c-436b-96a2-2cfb5f4e311a
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.SubscriptionResumeAt Property (WMI)
Specifies the number of remaining unconsumed messages at which message delivery is resumed to a subscription instance that has been paused because of a PauseAt setting.  
  
 The syntax shown is language neutral.  
  
## Syntax  
  
```  
uint32  SubscriptionResumeAt;  
```  
  
## Remarks  
 This property is read/write.  
  
 The default value of this property is 0.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.