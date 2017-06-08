---
title: "MSBTS_HostSetting.ThreadThreshold Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 37b07342-3d3b-4abb-adae-7b4ccb6309f4
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.ThreadThreshold Property (WMI)
This property lists the maximum number of threads in the process (per CPU) allowed before throttling begins.  
  
## Syntax  
  
```  
  
uint32ThreadThreshold;  
```  
  
## Remarks  
 The default value for this parameter is 0.  
  
 This property is read/write.  
  
 The syntax shown is language neutral.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.