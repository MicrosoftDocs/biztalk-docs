---
title: MSBTS_HostQueue.ResumeServiceInstancesByID Method (WMI)
TOCTitle: MSBTS_HostQueue.ResumeServiceInstancesByID Method (WMI)
ms:assetid: 48cc4259-c211-4423-94b0-6bc88edd952b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559938(v=BTS.80)
ms:contentKeyID: 51527789
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostQueue.ResumeServiceInstancesByID Method (WMI)

 

Resubmits service instances by ID.


> [!NOTE]
> <P>The syntax shown is language neutral.</P>



## Syntax

``` 
  
uint32 ResumeServiceInstancesByID(  
    string ServiceClassID[],  
    string ServiceTypeID[],  
    string ServiceInstanceID[],  
    uint32 ResumeMode  
);  
```

#### Parameters

*ServiceClassID*  
\[in\] An array of IDs of the service classes to which the message instance belongs.

*ServiceTypeID*  
\[in\] An array of IDs of the service types to which the message instance belongs.

*ServiceInstanceID*  
\[in\] An array of IDs of the service instance to which the message instance belongs.

*ResumeMode*  
\[in\] Use 1 to resume in regular non-debug mode, use 2 to resume in debug mode.

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Remarks

For more information about enumerating the **ServiceInstance** classes to construct an ID array to pass into this method, see [Resuming Suspended Service Instances of a Specific Orchestration Using WMI](resuming-suspended-service-instances-of-a-specific-orchestration-using-wmi.md).

The number of elements in *ServiceClassID*, *ServiceTypeID* and *ServiceInstanceID* parameters must be equal.

If you want to resume multiple instances, and if all instances have the same *ServiceClassID* or *ServiceTypeID*, passing a single value for either of these parameters while sending multiple values for *ServiceInstanceID* parameter is not supported.

A maximum of 2047 service instances can be resumed in a single **ResumeServiceInstancesByID** method call. To resume more than 2047 instances, enumerate the instances into batches of 2047, and then call the method on each batch.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

