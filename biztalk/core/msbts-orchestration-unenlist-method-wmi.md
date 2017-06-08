---
title: "MSBTS_Orchestration.Unenlist Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe227bda-072e-486d-8ebd-eada8ea6390c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Orchestration.Unenlist Method (WMI)
Terminates all instances of the orchestration and removes its activation subscription.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
uint32 UnenlistService(  
    uint32 AutoTerminateOrchestrationInstanceFlag  
);  
```  
  
#### Parameters  
 *AutoTerminateOrchestrationInstanceFlag*  
 [in] An **Integer** specifying whether instances of this orchestration type should be automatically terminated. Permissible values for this parameter are (1) "Do not terminate service instances of this orchestration," or (2) "Terminate all service instances of this orchestration." Note that the integer values must be used in code and script. The default value is 1.  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.