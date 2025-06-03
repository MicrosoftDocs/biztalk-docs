---
description: "Learn more about: MSBTS_ReceiveLocationOrchestration.OrchestrationAssemblyPublicKeyToken Property (WMI)"
title: MSBTS_ReceiveLocationOrchestration.OrchestrationAssemblyPublicKeyToken Property (WMI)
TOCTitle: MSBTS_ReceiveLocationOrchestration.OrchestrationAssemblyPublicKeyToken Property (WMI)
ms:assetid: db1280e6-fe35-4ce4-8a1c-cc76dfc928cf
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561406(v=BTS.80)
ms:contentKeyID: 51531764
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_ReceiveLocationOrchestration.OrchestrationAssemblyPublicKeyToken Property (WMI)

 

Contains the public key token of the Microsoft® .NET-based assembly with which this orchestration belongs.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string OrchestrationAssemblyPublicKeyToken;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, **OrchestrationAssemblyCulture**, **OrchestrationAssemblyName**, **OrchestrationAssemblyVersion**, **OrchestrationName**, **ReceiveLocationName**, and **ReceivePortName** this key forms a compound key for the class.

The maximum length for this property is 256 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

