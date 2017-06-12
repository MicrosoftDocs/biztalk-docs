---
title: "MSBTS_HostSetting.DeliveryQueueSize Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9be7f63e-9521-4d39-8c74-810a9b157805
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.DeliveryQueueSize Property (WMI)
This property represents the size of the in-memory queue. This queue serves as a temporary placeholder for delivering messages.  
  
## Syntax  
  
```  
  
uint32 DeliveryQueueSize;  
```  
  
## Remarks  
 The default value for this parameter is 100.  
  
 This property is read/write.  
  
 The syntax shown is language neutral.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.