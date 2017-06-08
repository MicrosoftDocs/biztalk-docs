---
title: "MSBTS_ServerHost.HostName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f1b11db-b823-4cf4-aa29-dbb95648ce1d
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ServerHost.HostName Property (WMI)
Contains the name of the host.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
string HostName;  
```  
  
## Remarks  
 This property is read-only.  
  
 This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **ServerName**, this key forms a compound key for the class.  
  
 The maximum length for this property is 80 characters.  
  
 For samples illustrating the **MSBTS_ServerHost** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.