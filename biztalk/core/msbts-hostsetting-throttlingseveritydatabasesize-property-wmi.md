---
title: "MSBTS_HostSetting.ThrottlingSeverityDatabaseSize Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff74a03c-fd19-4148-9f65-e65ef7f80213
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.ThrottlingSeverityDatabaseSize Property (WMI)
This property controls the severity of a database sized triggered throttling condition. This is specified in percentage value and this parameter sets the severity of a throttling condition caused when the message count in database threshold is exceeded.  
  
 The syntax shown is language neutral.  
  
## Syntax  
  
```  
uint32  ThrottlingSeverityDatabaseSize;  
```  
  
## Remarks  
 This property is read/write.  
  
 The default value of this property is 1.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.