---
title: MSBTS_ReceiveLocationOrchestration.OrchestrationAssemblyName Property (WMI)
TOCTitle: MSBTS_ReceiveLocationOrchestration.OrchestrationAssemblyName Property (WMI)
ms:assetid: 6faa19c4-1e0b-4077-a710-b78accf04fab
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560749(v=BTS.80)
ms:contentKeyID: 51528842
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocationOrchestration.OrchestrationAssemblyName Property (WMI)

 

Contains the name of the Microsoft® .NET-based assembly with which this orchestration belongs.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string OrchestrationAssemblyName;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, **OrchestrationAssemblyCulture**, **OrchestrationAssemblyPublicKeyToken**, **OrchestrationAssemblyVersion**, **OrchestrationName**, **ReceiveLocationName**, and **ReceivePortName** this key forms a compound key for the class.

The maximum length for this property is 256 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

