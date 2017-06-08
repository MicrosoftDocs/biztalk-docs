---
title: "MSBTS_SendPortGroup.Name Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a2b2e31-c75b-4f29-b0d2-ca927b449cd8
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendPortGroup.Name Property (WMI)
Contains the name of the send port group.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
string Name;  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **MgmtDBServerOverride**, this key forms a compound key for the class.  
  
 The maximum length for this property is 256 characters.  
  
 This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPortGroup.Name** property.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.