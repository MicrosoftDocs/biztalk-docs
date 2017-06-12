---
title: "MSBTS_GroupSetting.BizTalkB2BOperatorGroup Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac2be18f-e5d8-44b8-898f-7c89ecab5cfb
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_GroupSetting.BizTalkB2BOperatorGroup Property (WMI)
This property is the name of the BizTalk B2B Operators Windows Group.  Members of this Windows Group are granted permission to access BizTalk party/partners-related functions. Certain functions require additional Windows or SQL privileges; refer to the BizTalk Server Help for more details.  
  
## Syntax  
  
```  
  
string BizTalkB2BOperatorGroup;  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 The maximum length for this property is 128 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.