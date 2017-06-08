---
title: "MSBTS_ReceiveLocationOrchestration.OrchestrationAssemblyCulture Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8fee02af-71a5-4736-a7ee-dbe5894005fe
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveLocationOrchestration.OrchestrationAssemblyCulture Property (WMI)
Contains the culture of the Microsoft® .NET-based assembly with which this orchestration belongs.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string OrchestrationAssemblyCulture;  
```  
  
## Remarks  
 This property is read-only.  
  
 This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, **OrchestrationAssemblyName**, **OrchestrationAssemblyPublicKeyToken**, **OrchestrationAssemblyVersion**, **OrchestrationName**, **ReceiveLocationName**, and **ReceivePortName** this key forms a compound key for the class.  
  
 The maximum length for this property is 256 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.