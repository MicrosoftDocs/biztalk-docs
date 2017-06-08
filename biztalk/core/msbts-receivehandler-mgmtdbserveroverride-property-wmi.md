---
title: "MSBTS_ReceiveHandler.MgmtDbServerOverride Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ea637b5-ecac-460b-9338-ea9fadb59842
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveHandler.MgmtDbServerOverride Property (WMI)
Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string MgmtDbServerOverride = "";  
```  
  
## Remarks  
 This property is optional.  
  
 This property is read-write.  
  
 This property has a **Key** qualifier. Along with **AdapterName**, **HostName**, and **MgmtDbNameOverride**, this key forms a compound key for the class.  
  
 The maximum length for this property is 80 characters.  
  
 For samples illustrating the **MSBTS_ReceiveHandler** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.