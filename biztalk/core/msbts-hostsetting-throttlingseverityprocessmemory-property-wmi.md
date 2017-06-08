---
title: "MSBTS_HostSetting.ThrottlingSeverityProcessMemory Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3871300-a44f-49c3-91bf-f8e3a1cb0413
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.ThrottlingSeverityProcessMemory Property (WMI)
Controls the severity of a process memory triggered throttling condition. This is specified in percentage value and this parameter sets the severity of a throttling condition caused when the process memory usage threshold is exceeded.  
  
 The syntax shown is language neutral.  
  
## Syntax  
  
```  
uint32  ThrottlingSeverityProcessMemory;  
```  
  
## Remarks  
 This property is read/write.  
  
 The default value of this property is 500.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.