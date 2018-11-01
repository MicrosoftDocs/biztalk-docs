---
title: MSBTS_ReceiveLocationOrchestration.ReceivePortName Property (WMI)
TOCTitle: MSBTS_ReceiveLocationOrchestration.ReceivePortName Property (WMI)
ms:assetid: 50bd0cee-3f60-4736-be00-3a8b8541e47f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560127(v=BTS.80)
ms:contentKeyID: 51527999
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocationOrchestration.ReceivePortName Property (WMI)

 

Contains the name of receive port used by the given instance of the receive location.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string ReceivePortName;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, **OrchestrationAssemblyCulture**, **OrchestrationAssemblyName**, **OrchestrationAssemblyPublicKeyToken**, **OrchestrationAssemblyVersion**, **OrchestrationName**, and **ReceiveLocationName** this key forms a compound key for the class.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

