---
title: "MSBTS_ServiceInstance.ServiceStatus Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82ec2502-2df3-401c-a86e-9f41967d5076
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ServiceInstance.ServiceStatus Property (WMI)
Contains the state of the service instance to which this message belongs. The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
uint32 ServiceStatus;  
```  
  
## Remarks  
 This property is read-only.  
  
 The following table contains the permissible values for this property:  
  
|Description|Value|  
|-----------------|-----------|  
|Ready to run|1|  
|Active|2|  
|Suspended (resumable)|4|  
|Dehydrated|8|  
|Completed with discarded messages|16|  
|Suspended (not resumable)|32|  
|In breakpoint|64|  
  
 Note that the integer values must be used in code and script.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.