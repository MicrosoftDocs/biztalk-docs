---
title: "MSBTS_GroupSetting.PerfCounterCacheRefreshInterval Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d984a408-d4a8-498e-ab8c-71a08be87e1b
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_GroupSetting.PerfCounterCacheRefreshInterval Property (WMI)
This property indicates the interval at which performance counters are refreshed.  
  
 The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
uint32 PerfCounterCacheRefreshInterval;  
```  
  
## Remarks  
 This property is read-write.  
  
 If the in-memory size of a message batch reaches this threshold during processing, the portion of the message batch that has been processed is written to the MessageBox before the remainder of the message batch is processed.  
  
 The range for this property is 1 to 43200.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.