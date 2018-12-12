---
title: MSBTS_Orchestration.AssemblyPublicKeyToken Property (WMI)
TOCTitle: MSBTS_Orchestration.AssemblyPublicKeyToken Property (WMI)
ms:assetid: c25be2dc-f213-4e79-8f0d-98c7be523070
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547835(v=BTS.80)
ms:contentKeyID: 51531084
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Orchestration.AssemblyPublicKeyToken Property (WMI)

 

Contains the public key token of the .NET assembly to which this orchestration belongs.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string AssemblyPublicKeyToken;  
```

## Remarks

This property has a **Key** qualifier. Along with **AssemblyCulture**, **AssemblyName**, **AssemblyVersion**, **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **Name** this key forms a compound key for the class.

The maximum length for this property is 256 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

