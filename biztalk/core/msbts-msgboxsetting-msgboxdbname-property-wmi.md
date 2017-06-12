---
title: "MSBTS_MsgBoxSetting.MsgBoxDBName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61484743-9e16-465b-be0e-c085f82a3ce3
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_MsgBoxSetting.MsgBoxDBName Property (WMI)
Contains the name of the MessageBox setting database.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string MsgBoxDBName;  
```  
  
## Remarks  
 This property is read-only.  
  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **MsgBoxDBServerName**, this key forms a compound key for the class.  
  
 The maximum length for this property is 100 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.