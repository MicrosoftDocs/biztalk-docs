---
title: "MSBTS_HostQueue.TerminateServiceInstancesByID Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5982302-96eb-49ab-8f46-f5592aa3e0d6
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostQueue.TerminateServiceInstancesByID Method (WMI)
Terminates service instances by ID.  
  
> [!NOTE]
>  The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
uint32 TerminateServiceInstancesByID(  
    string ServiceClassID[],  
    string ServiceTypeID[],  
    string ServiceInstanceID[]  
);  
```  
  
#### Parameters  
 *ServiceClassID*  
 [in] An array of IDs of the service classes to which the message instance belongs.  
  
 *ServiceTypeID*  
 [in] An array of IDs of the service types to which the message instance belongs.  
  
 *ServiceInstanceID*  
 [in] An array of IDs of the service instances to which the message instance belongs.  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Remarks  
 For more information about enumerating the **ServiceInstance** classes to construct an ID array to pass into this method, see [Resuming Suspended Service Instances of a Specific Orchestration Using WMI](../core/resuming-suspended-service-instances-of-a-specific-orchestration-using-wmi.md).  
  
 The number of elements in *ServiceClassID*, *ServiceTypeID* and *ServiceInstanceID* parameters must be equal.  
  
 If you want to terminate multiple instances, and if all instances have the same *ServiceClassID* or *ServiceTypeID*, passing a single value for either of these parameters while sending multiple values for *ServiceInstanceID* parameter is not supported.  
  
 A maximum of 2047 service instances can be terminated in a single **TerminateServiceInstancesByID** method call. To terminate more than 2047 instances, enumerate the instances into batches of 2047, and then call the method on each batch.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.