---
title: MSBTS_Orchestration.AssemblyCulture Property (WMI)
TOCTitle: MSBTS_Orchestration.AssemblyCulture Property (WMI)
ms:assetid: cbfd855d-fd2d-497b-870e-38693d8d232e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa548028(v=BTS.80)
ms:contentKeyID: 51531241
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Orchestration.AssemblyCulture Property (WMI)

 

Contains the culture of the .NET assembly to which this orchestration belongs.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string AssemblyCulture;  
```

## Remarks

This property has a **Key** qualifier. Along with **AssemblyName**, **AssemblyPublicKeyToken**, **AssemblyVersion**, **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **Name** this key forms a compound key for the class.

The maximum length for this property is 256 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

