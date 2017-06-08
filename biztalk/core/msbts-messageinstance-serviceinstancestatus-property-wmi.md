---
title: "MSBTS_MessageInstance.ServiceInstanceStatus Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31964346-5411-4f3c-955e-5535c13c56bc
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_MessageInstance.ServiceInstanceStatus Property (WMI)
Contains state of the service instance to which this message belongs.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
uint32 ServiceInstanceStatus;  
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
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.