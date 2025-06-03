---
description: "Learn more about: MSBTS_Orchestration.Unenlist Method (WMI)"
title: MSBTS_Orchestration.Unenlist Method (WMI)
TOCTitle: MSBTS_Orchestration.Unenlist Method (WMI)
ms:assetid: fe227bda-072e-486d-8ebd-eada8ea6390c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa562143(v=BTS.80)
ms:contentKeyID: 51533758
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_Orchestration.Unenlist Method (WMI)

 

Terminates all instances of the orchestration and removes its activation subscription.

*The syntax shown is language neutral.*

## Syntax

```C#
  
uint32 UnenlistService(  
    uint32 AutoTerminateOrchestrationInstanceFlag  
);  
```

#### Parameters

*AutoTerminateOrchestrationInstanceFlag*  
\[in\] An **Integer** specifying whether instances of this orchestration type should be automatically terminated. Permissible values for this parameter are (1) "Do not terminate service instances of this orchestration," or (2) "Terminate all service instances of this orchestration." Note that the integer values must be used in code and script. The default value is 1.

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

