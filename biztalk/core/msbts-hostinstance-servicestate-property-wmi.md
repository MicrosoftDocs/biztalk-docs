---
title: "MSBTS_HostInstance.ServiceState Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 982db257-a2b7-4a39-994e-46d7cf333ea5
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstance.ServiceState Property (WMI)
Contains the state of the host instance.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
uint32 ServiceState;  
```  
  
## Remarks  
 This property is read only.  
  
 The following table contains the permissible values for this property:  
  
|Description|Value|  
|-----------------|-----------|  
|Stopped|1|  
|Start pending|2|  
|Stop pending|3|  
|Running|4|  
|Continue pending|5|  
|Pause pending|6|  
|Paused|7|  
|Unknown|8|  
  
 Note that the integer values must be used in code and script.  
  
 For samples illustrating the **MSBTS_HostInstance** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in  BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.