---
title: "MSBTS_GroupSetting.BizTalkAdministratorGroup Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d848685e-5156-4647-aa60-c42a6a03d70f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_GroupSetting.BizTalkAdministratorGroup Property (WMI)
Gets the name of the BizTalk Administrator Windows NT Group. Only members of this Windows NT Group have permissions to access BizTalk Administration functions.  
  
 The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
string BizTalkAdministratorGroup;  
```  
  
## Remarks  
 Only members of this Windows NT Group have permissions to access BizTalk Administration functions.  
  
 Certain functions require additional Windows or SQL privileges; refer to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help for more details.  
  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 Maximum length for this property is 63 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.