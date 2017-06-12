---
title: "MSBTS_SendPortGroup2SendPort.SendPortName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e69760ec-a6fe-4695-a9ed-044e2dcb452f
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendPortGroup2SendPort.SendPortName Property (WMI)
Contains the name of the send port.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string SendPortGroup;  
```  
  
## Remarks  
 This property is required for instance creation.  
  
 This property is read-only.  
  
 This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **SendPortGroupName**, this key forms a compound key for the class.  
  
 The maximum length for this property is 256 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.