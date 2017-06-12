---
title: "MSBTS_ReceiveHandler.AdapterName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4e2c0948-1358-488e-a137-dcca96976eb8
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveHandler.AdapterName Property (WMI)
Contains the name of the adapter.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string AdapterName;  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 This property has a Key qualifier. Along with **HostName**, **MgmtDbServerOverride**, and **MgmtDbNameOverride**, this key forms a compound key for the class.  
  
 The maximum length for this property is 256 characters.  
  
 For samples illustrating the **MSBTS_ReceiveHandler** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.