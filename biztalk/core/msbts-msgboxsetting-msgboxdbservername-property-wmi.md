---
title: "MSBTS_MsgBoxSetting.MsgBoxDBServerName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8573cbc4-a5dc-4ec8-87fa-37b35034d6f1
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_MsgBoxSetting.MsgBoxDBServerName Property (WMI)
Contains the name of the SQL Server where the MessageBox database is located.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string MsgBoxDBServerName;  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **MsgBoxDBName**, this key forms a compound key for the class.  
  
 The maximum length for this property is 80 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.