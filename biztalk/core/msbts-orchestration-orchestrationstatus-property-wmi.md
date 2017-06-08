---
title: "MSBTS_Orchestration.OrchestrationStatus Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bbe48cdb-e3d6-479c-b908-fc25d8d85632
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Orchestration.OrchestrationStatus Property (WMI)
Indicates the status of the orchestration.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
uint32 ServiceStatus;  
```  
  
## Remarks  
 This property is read-only.  
  
 The following table contains the permissible values for this property:  
  
|Description|Value|  
|-----------------|-----------|  
|Unbound|1|  
|Bound|2|  
|Stopped|3|  
|Started|4|  
  
 Note that the integer values must be used in code and script.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.