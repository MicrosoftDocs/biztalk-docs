---
title: "MSBTS_Server.MgmtDbServerOverride Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99f86602-cc5d-4410-93ac-1177dd4205a3
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Server.MgmtDbServerOverride Property (WMI)
Overrides the data source part of the BizTalk Management database connection string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.  
  
> [!NOTE]
>  The BizTalk Management database is also referred to as the BizTalk Configuration database.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
string MgmtDbServerOverride = "";  
```  
  
## Remarks  
 This property is optional.  
  
 This property is read-write.  
  
 This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **Name**, this key forms a compound key for the class.  
  
 The maximum length for this property is 80 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.