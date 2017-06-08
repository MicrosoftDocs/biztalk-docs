---
title: "MSBTS_HostInstance.Name Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9536d39-7837-48b0-b1e6-e4ab832dcc5f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstance.Name Property (WMI)
Contains the name of the host instance.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
string Name;  
```  
  
## Remarks  
 This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **MgmtDbServerOverride**, this key forms a compound key for the class.  
  
 The maximum length for this property is 128 characters.  
  
 For samples illustrating the **MSBTS_HostInstance** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.