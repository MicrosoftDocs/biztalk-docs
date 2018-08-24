---
title: MSBTS_ReceiveLocationOrchestration.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_ReceiveLocationOrchestration.MgmtDbNameOverride Property (WMI)
ms:assetid: f7a3cd00-9366-4e9a-96d8-e5a906eaa1bf
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561997(v=BTS.80)
ms:contentKeyID: 51533485
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocationOrchestration.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **MgmtDbServerOverride**, **OrchestrationAssemblyCulture**, OrchestrationAssemblyName, OrchestrationAssemblyPublicKeyToken, OrchestrationAssemblyVersion, **OrchestrationName**, **ReceiveLocationName**, and **ReceivePortName** this key forms a compound key for the class.

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

