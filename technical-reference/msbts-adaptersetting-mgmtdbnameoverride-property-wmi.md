---
description: "Learn more about: MSBTS_AdapterSetting.MgmtDbNameOverride Property (WMI)"
title: MSBTS_AdapterSetting.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_AdapterSetting.MgmtDbNameOverride Property (WMI)
ms:assetid: 2e3c86de-42ba-47db-8eff-7e71133addf9
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559414(v=BTS.80)
ms:contentKeyID: 51527050
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_AdapterSetting.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with [MgmtDbServerOverride](msbts-adaptersetting-mgmtdbserveroverride-property-wmi.md) and [Name](msbts-adaptersetting-name-property-wmi.md), this key forms a compound key for the class.

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

