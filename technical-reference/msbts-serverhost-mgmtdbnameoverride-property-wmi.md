---
description: "Learn more about: MSBTS_ServerHost.MgmtDbNameOverride Property (WMI)"
title: MSBTS_ServerHost.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_ServerHost.MgmtDbNameOverride Property (WMI)
ms:assetid: b8e9a348-44d9-442a-8aaa-f5f95b9d5113
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578298(v=BTS.80)
ms:contentKeyID: 51530805
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServerHost.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **HostName**, **MgmtDbServerOverride**, and **ServerName**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

For samples illustrating the **MSBTS\_ServerHost** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

