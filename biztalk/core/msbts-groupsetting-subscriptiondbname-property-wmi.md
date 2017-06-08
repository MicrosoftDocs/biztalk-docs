---
title: "MSBTS_GroupSetting.SubscriptionDBName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5af4eefa-9cac-4756-b311-d133ab0e1bd7
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_GroupSetting.SubscriptionDBName Property (WMI)
Gets the name of the master subscription SQL database.  
  
 The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
string SubscriptionDBName;  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 Maximum length for this property is 100 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.