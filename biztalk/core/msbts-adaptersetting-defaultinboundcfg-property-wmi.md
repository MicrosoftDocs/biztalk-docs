---
title: "MSBTS_AdapterSetting.DefaultInboundCfg Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f069e42-ad9b-46be-b1ac-5c41fa8d43a8
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_AdapterSetting.DefaultInboundCfg Property (WMI)
Gets a default inbound configuration for the adapter.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string DefaultInboundCfg;  
```  
  
## Remarks  
 This property is read-only.  
  
 The maximum length for this property is 1024 characters.  
  
 This configuration is used when a new [MSBTS_ReceiveHandler](../core/msbts-receivehandler-wmi.md) instance is created.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.