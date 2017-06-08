---
title: "MSBTS_HostSetting.HostTracking Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 79ed61fe-8cc3-44f6-aeb6-22cd460ebfcd
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.HostTracking Property (WMI)
Indicates whether instances of this BizTalk Host will host the tracking sub service.  
  
## Property Declaration  
 *The syntax shown is language neutral*.  
  
```  
boolean HostTracking = TRUE;  
```  
  
## Remarks  
 This property is read-write.  
  
 The default value for this property is **true**.  
  
 For sample code using the **MSBTS_HostSetting** class, see [Creating, Updating, and Deleting a Host Instance Using WMI](../core/creating-updating-and-deleting-a-host-instance-using-wmi.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.