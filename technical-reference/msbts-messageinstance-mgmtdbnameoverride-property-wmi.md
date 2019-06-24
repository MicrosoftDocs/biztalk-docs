---
title: MSBTS_MessageInstance.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_MessageInstance.MgmtDbNameOverride Property (WMI)
ms:assetid: 872af0b8-43c1-45ec-b092-4a1366c730f2
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561210(v=BTS.80)
ms:contentKeyID: 51529455
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_MessageInstance.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-only.

This property has a **Key** qualifier. Along with **MessageInstanceID**, **MgmtDbServerOverride**, and **ServiceInstanceID**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

