---
title: "MSBTS_Orchestration.AssemblyPublicKeyToken Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c25be2dc-f213-4e79-8f0d-98c7be523070
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Orchestration.AssemblyPublicKeyToken Property (WMI)
Contains the public key token of the .NET assembly to which this orchestration belongs.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string AssemblyPublicKeyToken;  
```  
  
## Remarks  
 This property has a **Key** qualifier. Along with **AssemblyCulture**, **AssemblyName**, **AssemblyVersion**, **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **Name** this key forms a compound key for the class.  
  
 The maximum length for this property is 256 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.