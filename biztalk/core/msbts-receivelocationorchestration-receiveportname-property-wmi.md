---
title: "MSBTS_ReceiveLocationOrchestration.ReceivePortName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50bd0cee-3f60-4736-be00-3a8b8541e47f
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveLocationOrchestration.ReceivePortName Property (WMI)
Contains the name of receive port used by the given instance of the receive location.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string ReceivePortName;  
```  
  
## Remarks  
 This property is read-only.  
  
 This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, **OrchestrationAssemblyCulture**, **OrchestrationAssemblyName**, **OrchestrationAssemblyPublicKeyToken**, **OrchestrationAssemblyVersion**, **OrchestrationName**, and **ReceiveLocationName** this key forms a compound key for the class.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.