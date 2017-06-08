---
title: "MSBTS_Orchestration.Stop Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 613b10af-c86e-432b-b6cd-ede1add9d57f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Orchestration.Stop Method (WMI)
Stops the orchestration by disabling its activation subscription.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
uint32 Stop(  
    uint32 AutoDisableReceiveLocationFlag,   
    uint32 AutoSuspendServiceInstanceFlag  
);  
```  
  
#### Parameters  
 *AutoDisableReceiveLocationFlag*  
 [in] Permissible values for this property are (1) "No auto disable of receive locations related to this Orchestration", or (2) "Disable all receive locations related to this orchestration that are not shared by other orchestration(s)". Note that the integer values must be used in code and script. The default value is 1.  
  
 *AutoSuspendOrchestrationInstanceFlag*  
 [in] Permissible values for this property are (1) "No auto suspend of service instances of this Orchestration", or (2) "Suspend all running service instances of this Orchestration". Note that the integer values must be used in code and script. The default value is 2.  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.