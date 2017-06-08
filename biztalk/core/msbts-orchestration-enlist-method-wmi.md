---
title: "MSBTS_Orchestration.Enlist Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6914664b-0017-41a2-a1c7-3732672c5620
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Orchestration.Enlist Method (WMI)
Enlists the orchestration by creating its activation subscription.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
uint32 Enlist(string ApplicationTypeName);  
```  
  
#### Parameters  
 *ApplicationTypeName*  
 [in] The application type name.  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.