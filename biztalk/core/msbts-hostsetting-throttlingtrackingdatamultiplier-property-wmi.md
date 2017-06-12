---
title: "MSBTS_HostSetting.ThrottlingTrackingDataMultiplier Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2362aaa6-7e9e-4587-bdeb-c1019563e0c3
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.ThrottlingTrackingDataMultiplier Property (WMI)
Specifies the factor by which the message count in database threshold will be multiplied and then compared against the current record count in the tracking table. This determines whether the system should throttle on tracking table size.  
  
## Syntax  
  
```vb  
uint32  ThrottlingTrackingDataMultiplier;  
```  
  
## Remarks  
 This property is read/write.  
  
 If this is set to 0, tracking table size is not used as a consideration for determining a throttling condition.  
  
 The default value of this property is 10. The maximum value is 1000.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.