---
title: "MSBTS_HostSetting.MessagingMaxReceiveInterval Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 06784349-d6e8-471c-8c12-3aa63dcaea7b
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.MessagingMaxReceiveInterval Property (WMI)
This property is the maximum polling interval in milliseconds that the BizTalk host instance looks for new messages. Allowed values are 50 to int max.  
  
## Syntax  
  
```vb  
uint32  MessagingMaxReceiveInterval;  
```  
  
## Remarks  
 This property is read/write.  
  
 The default value for this property is 500.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.