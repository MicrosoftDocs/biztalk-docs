---
title: "MSBTS_HostSetting.ProcessMemoryThreshold Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e403eec-e59e-4603-84db-370c7ba8cb6b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.ProcessMemoryThreshold Property (WMI)
This property represents the maximum Process Memory (in percent) allowed before throttling begins (in percent or megabytes).  
  
 Set to 0 to disable throttling that is based on process memory. If you provide a percent value (a value between 1 and 100), the threshold is set to the percentage value of the total virtual memory available to the process, including available physical memory, available page-file, memory already allocated to the process, memory addressing limits such as the 2 gigabyte addressing limit for 32-bit memory-addressing architecture, and so forth. When you specify a percent value, the process memory threshold is computed dynamically at regular periodic intervals. If a value above 100 is specified, the threshold will be set to this value in megabytes.  
  
## Syntax  
  
```  
  
uint32ProcessMemoryThreshold;  
```  
  
## Remarks  
 The default value for this parameter is 25.  
  
 This property is read/write.  
  
 The syntax shown is language neutral.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.