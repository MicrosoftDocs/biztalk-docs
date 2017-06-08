---
title: "MSBTS_HostSetting.XlangMaxReceiveInterval Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e6a5762-49f7-4db3-b07d-9d8c13de320f
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.XlangMaxReceiveInterval Property (WMI)
This property is the maximum polling interval in milliseconds that the BizTalk host instance looks for new messages in XLANG. Allowed values are 50 to int max.  
  
## Syntax  
  
```vb  
uint32  XlangMaxReceiveInterval;  
```  
  
## Remarks  
 This property is read/write.  
  
 The default value for this property is 500.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.