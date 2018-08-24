---
title: MSBTS_Orchestration.AssemblyVersion Property (WMI)
TOCTitle: MSBTS_Orchestration.AssemblyVersion Property (WMI)
ms:assetid: d2e007a1-78a3-4020-9f15-47a947b4a275
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578569(v=BTS.80)
ms:contentKeyID: 51531447
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Orchestration.AssemblyVersion Property (WMI)

 

Contains the version of the .NET assembly to which this orchestration belongs.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string AssemblyVersion;  
```

## Remarks

This property has a **Key** qualifier. Along with **AssemblyCulture**, **AssemblyName**, **AssemblyPublicKeyToken**, **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **Name** this key forms a compound key for the class.

The maximum length for this property is 256 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

