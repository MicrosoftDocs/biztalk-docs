---
title: "MSBTS_GroupSetting.MgmtDbName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1e56ac5-5fc7-4c09-ad18-1498c7c41327
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_GroupSetting.MgmtDbName Property (WMI)
Gets the initial catalog part of the BizTalk Management database connect string, and represents the database name.  
  
 The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
string MgmtDbName = "";  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 This property has a **Key** qualifier. Along with **MgmtDbServerName**, this key forms a compound key for the class.  
  
 Maximum length for this property is 123 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.