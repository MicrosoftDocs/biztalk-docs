---
title: "MSBTS_HostSetting.ThrottlingBatchMemoryThresholdPercent Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2a4b690-bc44-4e67-9580-380186f6f78a
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.ThrottlingBatchMemoryThresholdPercent Property (WMI)
Specifies the batch memory threshold. The batch memory threshold is the percentage of the process memory threshold beyond which to throttle the publishing of a batch of messages.  
  
## Syntax  
  
```vb  
uint32  ThrottlingBatchMemoryThresholdPercent;  
```  
  
## Remarks  
 This property is read/write.  
  
 If the memory estimated to execute a publishing batch exceeds the batch memory threshold, the batch will be subject to process memory based throttling. Otherwise, the batch will be exempt from process memory based throttling, even when the total process memory exceeds the process memory usage threshold.  
  
 The default value of this property is 1. The minimum value is 0, indicating that all publishing batches may be subject to process memory based throttling, even if the memory estimated to execute the batch is minimal. The maximum value is 100.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.