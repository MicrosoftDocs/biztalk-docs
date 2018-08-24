---
title: MSBTS_Orchestration.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_Orchestration.MgmtDbNameOverride Property (WMI)
ms:assetid: b5d4d7d5-fc87-4308-b204-a61977791028
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578237(v=BTS.80)
ms:contentKeyID: 51530729
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Orchestration.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **AssemblyCulture**, **AssemblyName**, **AssemblyPublicKeyToken**, **AssemblyVersion**, **MgmtDbServerOverride**, and **Name** this key forms a compound key for the class.

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

