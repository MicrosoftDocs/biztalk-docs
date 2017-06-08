---
title: "MSBTS_HostQueue.MgmtDbServerOverride Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13b369e3-8ba2-4414-8368-5268c873c827
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostQueue.MgmtDbServerOverride Property (WMI)
Overrides the data source part of the BizTalk Managemetn database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.  
  
> [!NOTE]
>  The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
string MgmtDbServerOverride = "";  
```  
  
## Remarks  
 This property is optional.  
  
 This property is read-only.  
  
 This property has a **Key** qualifier. Along with **HostName** and **MgmtDbNameOverride**, this key forms a compound key for the class.  
  
 The maximum length for this property is 80 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.