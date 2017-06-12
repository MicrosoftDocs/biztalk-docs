---
title: "MSBTS_ReceiveLocationOrchestration.OrchestrationStatus Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6450b2f8-7e1d-4457-a686-9316afa1bc1b
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveLocationOrchestration.OrchestrationStatus Property (WMI)
Indicates the status of the orchestration.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
uint32 OrchestrationStatus;  
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
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.