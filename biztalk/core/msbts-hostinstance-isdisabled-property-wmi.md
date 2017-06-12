---
title: "MSBTS_HostInstance.IsDisabled Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b22d8b0b-81ef-4e07-a058-3eb5ddeecc61
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstance.IsDisabled Property (WMI)
Enables or disables a host instance.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
boolean IsDisabled = FALSE;  
```  
  
## Remarks  
 **IsDisabled** can only be set when the host instance is in a stopped state.  
  
 For samples illustrating the **MSBTS_HostInstance** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.