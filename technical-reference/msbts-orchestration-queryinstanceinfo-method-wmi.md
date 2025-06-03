---
description: "Learn more about: MSBTS_Orchestration.QueryInstanceInfo Method (WMI)"
title: MSBTS_Orchestration.QueryInstanceInfo Method (WMI)
TOCTitle: MSBTS_Orchestration.QueryInstanceInfo Method (WMI)
ms:assetid: 3e9944ca-231e-44f7-a6c4-e39cb02bf9cd
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559739(v=BTS.80)
ms:contentKeyID: 51527547
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_Orchestration.QueryInstanceInfo Method (WMI)

 

Retrieves information about instances of the orchestration in various states.

*The syntax shown is language neutral.*

## Syntax

```C#
  
uint32 QueryInstanceInfo(  
    uint32 NumberOfRunningActiveInstances,  
    uint32 NumberOfRunningDehydratedInstances,  
    uint32 NumberOfSuspendedInstances  
);  
```

#### Parameters

*NumberOfRunningActiveInstances*  
\[out\] An **Integer** containing the number of running active instances.

*NumberOfRunningDehydratedInstances*  
\[out\] An **Integer** containing the number of running dehydrated instances.

*NumberOfSuspendedInstances*  
\[out\] An **Integer** containing the number of suspended instances.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

