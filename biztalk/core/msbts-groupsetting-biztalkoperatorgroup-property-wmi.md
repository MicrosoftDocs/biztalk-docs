---
title: "MSBTS_GroupSetting.BizTalkOperatorGroup Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41cffc6e-e587-47c9-a5f7-5d2f6c6fbe84
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_GroupSetting.BizTalkOperatorGroup Property (WMI)
This property is the name of the BizTalk Operators Windows Group.  Members of this Windows Group are granted permission to access BizTalk Monitoring functions. Certain functions require additional Windows or SQL privileges in addition to those granted by this group.  
  
## Syntax  
  
```  
  
string BizTalkOperatorGroup;  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 The maximum length for this property is 128 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.