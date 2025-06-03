---
description: "Learn more about: MSBTS_ReceiveLocationOrchestration.MgmtDbServerOverride Property (WMI)"
title: MSBTS_ReceiveLocationOrchestration.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_ReceiveLocationOrchestration.MgmtDbServerOverride Property (WMI)
ms:assetid: c88ed607-b699-4dc1-8c0b-1e617741ef91
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547968(v=BTS.80)
ms:contentKeyID: 51531138
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_ReceiveLocationOrchestration.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **OrchestrationAssemblyCulture**, OrchestrationAssemblyName, OrchestrationAssemblyPublicKeyToken, OrchestrationAssemblyVersion, **OrchestrationName**, **ReceiveLocationName**, and **ReceivePortName** this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

