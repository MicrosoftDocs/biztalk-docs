---
description: "Learn more about: MSBTS_HostQueue.SuspendServiceInstancesByID Method (WMI)"
title: MSBTS_HostQueue.SuspendServiceInstancesByID Method (WMI)
TOCTitle: MSBTS_HostQueue.SuspendServiceInstancesByID Method (WMI)
ms:assetid: c59e21d2-b63a-47ed-bc8d-5662e053af33
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547906(v=BTS.80)
ms:contentKeyID: 51531183
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_HostQueue.SuspendServiceInstancesByID Method (WMI)

 

Moves service instance IDs to the suspended queue.


> [!NOTE]
> <P>The syntax shown is language neutral.</P>



## Syntax

```C#
  
uint32 SuspendServiceInstancesByID(  
    string ServiceClassID[],  
    string ServiceTypeID[],  
    string ServiceInstanceID[]  
);  
```

#### Parameters

*ServiceClassID*  
\[in\] An array of IDs of the service classes to which the message instance belongs.

*ServiceTypeID*  
\[in\] An array of IDs of the service types to which the message instance belongs.

*ServiceInstanceID*  
\[in\] An array of IDs of the service instances to which the message instance belongs.

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Remarks

For more information about enumerating the **ServiceInstance** classes to construct an ID array to pass into this method, see [Resuming Suspended Service Instances of a Specific Orchestration Using WMI](resuming-suspended-service-instances-of-a-specific-orchestration-using-wmi.md).

The number of elements in *ServiceClassID*, *ServiceTypeID* and *ServiceInstanceID* parameters must be equal.

If you want to suspend multiple instances, and if all instances have the same *ServiceClassID* or *ServiceTypeID*, passing a single value for either of these parameters while sending multiple values for *ServiceInstanceID* parameter is not supported.

A maximum of 2047 service instances can be suspended in a single **SuspendServiceInstancesByID** method call. To suspend more than 2047 instances, enumerate the instances into batches of 2047, and then call the method on each batch.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

