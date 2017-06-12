---
title: "MSBTS_TrackedMessageInstance2.MgmtDbNameOverride Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 400c9b09-ce2a-4a52-b129-450d7984ef12
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_TrackedMessageInstance2.MgmtDbNameOverride Property (WMI)
This optional property can be used to override the initial catalog part of the BizTalk Messaging Management database connect string, and represents the database name.  
  
## Syntax  
  
```  
  
string MgmtDbNameOverride;  
```  
  
## Remarks  
 This parameter is read/write.  
  
 The syntax shown is language neutral.  
  
 The default value for this parameter is "".  
  
 The maximum length for this parameter is 123 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.