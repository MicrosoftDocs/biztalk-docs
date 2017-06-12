---
title: "MSBTS_HostSetting.DehydrationBehavior Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b672a19-0080-4025-8b6d-80e4a6056f40
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.DehydrationBehavior Property (WMI)
This property controls the dehydration behavior of the orchestration (XLANG) engine. Other XLANG settings should only be editable if the value is Custom.  
  
## Syntax  
  
```  
uint32  DehydrationBehavior;  
```  
  
## Property Value/Return Value  
 Values: 0 = Always; 1 = Never; 2 = Custom.  
  
## Remarks  
 This property is read/write.  
  
 The default value of this property is 2 (Custom).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.