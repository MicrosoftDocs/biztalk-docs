---
description: "Learn more about: MSBTS_HostInstance.MgmtDbNameOverride Property (WMI)"
title: MSBTS_HostInstance.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_HostInstance.MgmtDbNameOverride Property (WMI)
ms:assetid: 496f7e8c-f623-4c77-ac7d-cf54bfcca922
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559957(v=BTS.80)
ms:contentKeyID: 51527802
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_HostInstance.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property has a **Key** qualifier. Along with **Name** and **MgmtDbNameOverride**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

For samples illustrating the **MSBTS\_HostInstance** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

