---
title: "MSBTS_HostInstanceSetting.Name Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a3bcfcd-3fa9-41d1-9d46-d663a4ef68fb
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstanceSetting.Name Property (WMI)
Contains the name of the host instance.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
string Name;  
```  
  
## Remarks  
 This property is read-only.  
  
 The value of **Name** is unique in the BizTalk group.  
  
 This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **MgmtDbServerOverride**, this key forms a compound key for the class.  
  
 The maximum length for this property is 128 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.