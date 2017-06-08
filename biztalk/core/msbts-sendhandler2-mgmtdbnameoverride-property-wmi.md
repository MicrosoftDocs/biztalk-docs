---
title: "MSBTS_SendHandler2.MgmtDbNameOverride Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 303efd7c-d33b-4253-8b36-398587494ec2
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendHandler2.MgmtDbNameOverride Property (WMI)
This optional property can be used to override the initial catalog part of the BizTalk Messaging Management database connect string, and represents the database name. Max length for this property is 123 characters.  
  
 string MgmtDbNameOverride="";  
  
## Syntax  
  
```  
  
string MgmtDbNameOverride;  
```  
  
## Remarks  
 This property is read/write.  
  
 The syntax shown is language neutral.  
  
 The default value for this property is "".  
  
 The maximum length for this property is 123 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.