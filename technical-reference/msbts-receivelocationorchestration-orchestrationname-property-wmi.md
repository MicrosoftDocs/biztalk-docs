---
title: MSBTS_ReceiveLocationOrchestration.OrchestrationName Property (WMI)
TOCTitle: MSBTS_ReceiveLocationOrchestration.OrchestrationName Property (WMI)
ms:assetid: 29273a7c-f09f-44af-8ca0-8830525ed7c9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559312(v=BTS.80)
ms:contentKeyID: 51526894
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocationOrchestration.OrchestrationName Property (WMI)

 

Contains the name of the orchestration.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string OrchestrationName;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, **OrchestrationAssemblyCulture**, **OrchestrationAssemblyName**, **OrchestrationAssemblyPublicKeyToken**, **OrchestrationAssemblyVersion**, **ReceiveLocationName**, and **ReceivePortName** this key forms a compound key for the class.

The maximum length for this property is 256 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

