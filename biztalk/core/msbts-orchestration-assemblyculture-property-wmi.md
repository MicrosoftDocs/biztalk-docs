---
title: "MSBTS_Orchestration.AssemblyCulture Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cbfd855d-fd2d-497b-870e-38693d8d232e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Orchestration.AssemblyCulture Property (WMI)
Contains the culture of the .NET assembly to which this orchestration belongs.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string AssemblyCulture;  
```  
  
## Remarks  
 This property has a **Key** qualifier. Along with **AssemblyName**, **AssemblyPublicKeyToken**, **AssemblyVersion**, **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **Name** this key forms a compound key for the class.  
  
 The maximum length for this property is 256 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.