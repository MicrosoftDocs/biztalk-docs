---
title: "MSBTS_MessageInstance.ServiceInstanceID Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27bff459-aab7-4c87-b1a9-b42d7358f6bd
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_MessageInstance.ServiceInstanceID Property (WMI)
Contains the ID of the service instance to which the message instance belongs.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string ServiceInstanceID;  
```  
  
## Remarks  
 This property is read-only.  
  
 This property has a **Key** qualifier. Along with **MessageInstanceID**, **MgmtDbNameOverride**, and **MgmtDbServerOverride**, this key forms a compound key for the class.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.