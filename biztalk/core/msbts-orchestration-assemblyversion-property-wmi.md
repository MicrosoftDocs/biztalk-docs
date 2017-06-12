---
title: "MSBTS_Orchestration.AssemblyVersion Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d2e007a1-78a3-4020-9f15-47a947b4a275
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Orchestration.AssemblyVersion Property (WMI)
Contains the version of the .NET assembly to which this orchestration belongs.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string AssemblyVersion;  
```  
  
## Remarks  
 This property has a **Key** qualifier. Along with **AssemblyCulture**, **AssemblyName**, **AssemblyPublicKeyToken**, **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **Name** this key forms a compound key for the class.  
  
 The maximum length for this property is 256 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.