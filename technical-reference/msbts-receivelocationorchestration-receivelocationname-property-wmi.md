---
title: MSBTS_ReceiveLocationOrchestration.ReceiveLocationName Property (WMI)
TOCTitle: MSBTS_ReceiveLocationOrchestration.ReceiveLocationName Property (WMI)
ms:assetid: cd427711-842e-4afb-aef0-c545a77631f5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa548065(v=BTS.80)
ms:contentKeyID: 51531290
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocationOrchestration.ReceiveLocationName Property (WMI)

 

Contains the name of the receive location.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string ReceiveLocationName;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, **OrchestrationAssemblyCulture**, **OrchestrationAssemblyName**, **OrchestrationAssemblyPublicKeyToken**, **OrchestrationAssemblyVersion**, **OrchestrationName**, and **ReceivePortName** this key forms a compound key for the class.

The maximum length for this property is 256 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

