---
title: "MSBTS_Orchestration.QueryInstanceInfo Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e9944ca-231e-44f7-a6c4-e39cb02bf9cd
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Orchestration.QueryInstanceInfo Method (WMI)
Retrieves information about instances of the orchestration in various states.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
uint32 QueryInstanceInfo(  
    uint32 NumberOfRunningActiveInstances,  
    uint32 NumberOfRunningDehydratedInstances,  
    uint32 NumberOfSuspendedInstances  
);  
```  
  
#### Parameters  
 *NumberOfRunningActiveInstances*  
 [out] An **Integer** containing the number of running active instances.  
  
 *NumberOfRunningDehydratedInstances*  
 [out] An **Integer** containing the number of running dehydrated instances.  
  
 *NumberOfSuspendedInstances*  
 [out] An **Integer** containing the number of suspended instances.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.