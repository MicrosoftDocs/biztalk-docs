---
title: "MSBTS_HostSetting.ThrottlingLimitToTriggerGC Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d677733d-a88b-4acf-a325-b099e0224de5
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.ThrottlingLimitToTriggerGC Property (WMI)
Specifies the percentage of the process memory consumption threshold at which a .NET Framework garbage collection (GC) will be triggered.  
  
## Syntax  
  
```vb  
uint32  ThrottlingLimitToTriggerGC;  
```  
  
## Remarks  
 This property is read/write.  
  
 The default value of this property is 80. The minimum value is 50 and the maximum value is 100.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.