---
title: "MSBTS_HostSetting.AuthTrusted Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe05f006-9473-47b6-8a36-630bb19c5f80
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.AuthTrusted Property (WMI)
Indicates whether a BizTalk host can be trusted to collect authentication information.  
  
## Property Declaration  
 *The syntax shown is language neutral*.  
  
```  
boolean AuthTrusted = false;  
```  
  
## Remarks  
 This property is read-write.  
  
 The default value for this property is **false**.  
  
 For sample code using the **MSBTS_HostSetting** class, see [Creating, Updating, and Deleting a Host Instance Using WMI](../core/creating-updating-and-deleting-a-host-instance-using-wmi.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.