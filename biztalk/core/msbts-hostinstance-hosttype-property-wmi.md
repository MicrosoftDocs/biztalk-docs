---
title: "MSBTS_HostInstance.HostType Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc7031d7-7c22-467a-a979-d7058227a2cb
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstance.HostType Property (WMI)
Indicates which runtime model the instances of the BizTalk host will be running in. The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
uint32 HostType;  
```  
  
## Remarks  
 This property is read only.  
  
 The following table contains the permissible values for this property:  
  
|Description|Value|  
|-----------------|-----------|  
|In-process|1|  
|Isolated|2|  
  
 Note that the integer values must be used in code and script.  
  
 For samples illustrating the **MSBTS_HostInstance** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.