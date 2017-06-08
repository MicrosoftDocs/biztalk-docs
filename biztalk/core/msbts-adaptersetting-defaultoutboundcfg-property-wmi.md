---
title: "MSBTS_AdapterSetting.DefaultOutboundCfg Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63ccfec4-2e9e-4ed0-b041-677ac8425da5
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_AdapterSetting.DefaultOutboundCfg Property (WMI)
Gets a default outbound configuration for the adapter.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string DefaultOutboundCfg;  
```  
  
## Remarks  
 This property is read-only.  
  
 The maximum length for this property is 1024 characters.  
  
 This configuration is used when a new [MSBTS_SendHandler](../core/msbts-sendhandler-wmi.md) instance is created.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.