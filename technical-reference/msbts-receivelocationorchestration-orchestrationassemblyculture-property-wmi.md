---
description: "Learn more about: MSBTS_ReceiveLocationOrchestration.OrchestrationAssemblyCulture Property (WMI)"
title: MSBTS_ReceiveLocationOrchestration.OrchestrationAssemblyCulture Property (WMI)
TOCTitle: MSBTS_ReceiveLocationOrchestration.OrchestrationAssemblyCulture Property (WMI)
ms:assetid: 8fee02af-71a5-4736-a7ee-dbe5894005fe
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561363(v=BTS.80)
ms:contentKeyID: 51529666
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocationOrchestration.OrchestrationAssemblyCulture Property (WMI)

 

Contains the culture of the Microsoft® .NET-based assembly with which this orchestration belongs.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string OrchestrationAssemblyCulture;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, **OrchestrationAssemblyName**, **OrchestrationAssemblyPublicKeyToken**, **OrchestrationAssemblyVersion**, **OrchestrationName**, **ReceiveLocationName**, and **ReceivePortName** this key forms a compound key for the class.

The maximum length for this property is 256 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

