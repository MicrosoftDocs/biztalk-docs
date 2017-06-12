---
title: "MSBTS_HostInstanceSetting.ConfigurationState Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8b0ab09-a8b4-43cb-9cc4-f56f5deafe48
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstanceSetting.ConfigurationState Property (WMI)
Contains the installation state for given instance of the BizTalk host.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
uint32 ConfigurationState;  
```  
  
## Remarks  
 This property is read-only.  
  
 The following table contains the permissible values for this property:  
  
|Description|Value|  
|-----------------|-----------|  
|Installed|1|  
|Installation failed|2|  
|Uninstallation failed|3|  
|Update failed|4|  
|Not installed|5|  
  
 Note that the integer values must be used in code and script.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.