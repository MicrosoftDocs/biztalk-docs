---
title: "MSBTS_ServerHost.ServerName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53c15dc0-3386-42c9-9451-65954f1356ac
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ServerHost.ServerName Property (WMI)
Contains the name of the server.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
string ServerName;  
```  
  
## Remarks  
 This property is read-only.  
  
 This property has a **Key** qualifier. Along with **HostName**, **MgmtDbNameOverride**, and **MgmtDbServerOverride**, this key forms a compound key for the class.  
  
 The maximum length for this property is 63 characters.  
  
 For samples illustrating the **MSBTS_ServerHost** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.