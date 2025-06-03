---
description: "Learn more about: MSBTS_ReceiveLocationOrchestration.OrchestrationAssemblyVersion Property (WMI)"
title: MSBTS_ReceiveLocationOrchestration.OrchestrationAssemblyVersion Property (WMI)
TOCTitle: MSBTS_ReceiveLocationOrchestration.OrchestrationAssemblyVersion Property (WMI)
ms:assetid: 563b27c9-f2ad-450c-849c-d94e4a4d8e0e
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560239(v=BTS.80)
ms:contentKeyID: 51528144
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_ReceiveLocationOrchestration.OrchestrationAssemblyVersion Property (WMI)

 

Contains the version of the Microsoft® .NET-based assembly with which this orchestration belongs.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string OrchestrationAssemblyName;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, **OrchestrationAssemblyCulture**, **OrchestrationAssemblyName**, **OrchestrationAssemblyPublicKeyToken**, **OrchestrationName**, **ReceiveLocationName**, and **ReceivePortName** this key forms a compound key for the class.

The maximum length for this property is 256 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

