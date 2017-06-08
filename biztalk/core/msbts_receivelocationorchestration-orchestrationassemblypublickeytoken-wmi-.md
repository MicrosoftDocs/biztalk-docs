---
title: "MSBTS_ReceiveLocationOrchestration.OrchestrationAssemblyPublicKeyToken Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: db1280e6-fe35-4ce4-8a1c-cc76dfc928cf
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveLocationOrchestration.OrchestrationAssemblyPublicKeyToken Property (WMI)
Contains the public key token of the Microsoft® .NET-based assembly with which this orchestration belongs.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string OrchestrationAssemblyPublicKeyToken;  
```  
  
## Remarks  
 This property is read-only.  
  
 This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, **OrchestrationAssemblyCulture**, **OrchestrationAssemblyName**, **OrchestrationAssemblyVersion**, **OrchestrationName**, **ReceiveLocationName**, and **ReceivePortName** this key forms a compound key for the class.  
  
 The maximum length for this property is 256 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.