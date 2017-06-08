---
title: "MSBTS_SendHandler.MgmtDbServerOverride Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6cffe8de-17d8-4f62-ad0c-110c4900c526
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendHandler.MgmtDbServerOverride Property (WMI)
Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string MgmtDbServerOverride = "";  
```  
  
## Remarks  
 This property is optional.  
  
 This property is read-write.  
  
 This property has a **Key** qualifier. Along with **AdapterName** and **MgmtDbNameOverride**, this key forms a compound key for the class.  
  
 The maximum length for this property is 80 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.