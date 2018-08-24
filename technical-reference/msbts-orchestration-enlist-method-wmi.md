---
title: MSBTS_Orchestration.Enlist Method (WMI)
TOCTitle: MSBTS_Orchestration.Enlist Method (WMI)
ms:assetid: 6914664b-0017-41a2-a1c7-3732672c5620
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560599(v=BTS.80)
ms:contentKeyID: 51528664
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Orchestration.Enlist Method (WMI)

 

Enlists the orchestration by creating its activation subscription.

*The syntax shown is language neutral.*

## Syntax

``` 
  
uint32 Enlist(string ApplicationTypeName);  
```

#### Parameters

*ApplicationTypeName*  
\[in\] The application type name.

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

