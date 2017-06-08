---
title: "MSBTS_GroupSetting.SubscriptionDBServerName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ac5a718-ddb9-4307-a3e7-0d24b0dd7e98
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_GroupSetting.SubscriptionDBServerName Property (WMI)
Gets the name of the server running SQL Server where master subscription database is located.  
  
 The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
string SubscriptionDBServerName;  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 Maximum length for this property is 80 characters  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.