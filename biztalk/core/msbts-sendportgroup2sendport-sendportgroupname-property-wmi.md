---
title: "MSBTS_SendPortGroup2SendPort.SendPortGroupName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b4fc74c9-9b0c-413e-92ab-b5acd8baedd6
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendPortGroup2SendPort.SendPortGroupName Property (WMI)
Contains the name of the send port group.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string SendPortGroupName;  
```  
  
## Remarks  
 This property is required for instance creation.  
  
 This property is read-only.  
  
 This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **SendPortName**, this key forms a compound key for the class.  
  
 The maximum length for this property is 256 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.