---
title: "MSBTS_HostSetting.DBSessionThreshold Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 32725bbb-b78b-42f7-bde1-fb06a668481a
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.DBSessionThreshold Property (WMI)
This parameter represents the maximum number of DB Sessions (per CPU) allowed before throttling begins.  
  
## Syntax  
  
```  
  
uint32DBSessionThreshold;  
```  
  
## Remarks  
 The default value for this parameter is 0.  
  
 This property is read/write.  
  
 The syntax shown is language neutral.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.