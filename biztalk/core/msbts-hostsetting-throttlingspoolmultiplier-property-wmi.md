---
title: "MSBTS_HostSetting.ThrottlingSpoolMultiplier Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5fb1531-f8cc-4270-ada8-3069ab37acf3
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.ThrottlingSpoolMultiplier Property (WMI)
Specifies the factor by which the message count in database threshold will be multiplied and then compared against the current record count in the spool table. This determines whether the system should throttle on spool table size.  
  
## Syntax  
  
```vb  
uint32  ThrottlingSpoolMultiplier;  
```  
  
## Remarks  
 This property is read/write.  
  
 If this is set to 0, spool table size is not used as a consideration for determining a throttling condition.  
  
 The default value of this property is 10. The maximum value is 1000.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.