---
title: "MSBTS_ReceiveLocation.OperatingWindowEnabled (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4c5f567-be5a-4154-94c0-99e5b92ea778
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveLocation.OperatingWindowEnabled (WMI)
Enables or disables a service window, which is defined by the **SrvWinStartDT** and **SrvWinStopDT** properties.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
boolean ServiceWindowEnabled = FALSE;  
```  
  
## Remarks  
 This property is read-write.  
  
 The default value for this property is **FALSE**.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.