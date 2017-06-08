---
title: "MSBTS_Host.MgmtDbServerOverride Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a1a5f4b-006e-4d76-9897-0e2a6b342b32
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Host.MgmtDbServerOverride Property (WMI)
Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
string MgmtDbServerOverride = "";  
```  
  
## Remarks  
 This property is optional.  
  
 This property is read-write.  
  
 This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **Name**, this key forms a compound key for the class.  
  
 The maximum length for this property is 80 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.