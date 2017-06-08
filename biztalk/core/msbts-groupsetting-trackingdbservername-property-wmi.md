---
title: "MSBTS_GroupSetting.TrackingDBServerName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5d0d3a47-a454-4f50-9ba6-5d61b9c6016b
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_GroupSetting.TrackingDBServerName Property (WMI)
Gets the name of SQL Server where the tracking database is located.  
  
 The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
string TrackingDBServerName;  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 Maximum length for this property is 80 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.