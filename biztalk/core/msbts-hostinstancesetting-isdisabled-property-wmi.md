---
title: "MSBTS_HostInstanceSetting.IsDisabled Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 494a073c-0f23-465a-93bf-cf7d84cf9d94
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstanceSetting.IsDisabled Property (WMI)
Enables or disables a host instance.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
boolean IsDisabled = FALSE;  
```  
  
## Remarks  
 The **IsDisabled** property can be changed when the host instance is in the stopped or started state. However, if a host instance is disabled while it is running, then the change will not take effect until the host instance is stopped. Thus a running host instance will continue to run even if it is disabled. But once it is stopped, you cannot start it until the **IsDisabled** property is set to FALSE again.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.