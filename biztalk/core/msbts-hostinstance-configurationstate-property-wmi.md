---
title: "MSBTS_HostInstance.ConfigurationState Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63ba5883-31c2-4604-8e90-e69cd9418d63
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstance.ConfigurationState Property (WMI)
Contains the installation state for given instance of the BizTalk host.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
uint32 ConfigurationState;  
```  
  
## Remarks  
 This property is read only.  
  
 The following table contains the permissible values for this property:  
  
|Description|Value|  
|-----------------|-----------|  
|Installed|1|  
|Installation failed|2|  
|Uninstallation failed|3|  
|Update failed|4|  
|Not installed|5|  
  
 Note that the integer values must be used in code and script.  
  
 For samples illustrating the **MSBTS_HostInstance** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.