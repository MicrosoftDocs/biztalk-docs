---
description: "Learn more about: MSBTS_ReceiveHandler.MgmtDbNameOverride Property (WMI)"
title: MSBTS_ReceiveHandler.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_ReceiveHandler.MgmtDbNameOverride Property (WMI)
ms:assetid: 528a829f-5a78-4568-a618-84f155a34d3f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560162(v=BTS.80)
ms:contentKeyID: 51528044
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_ReceiveHandler.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **AdapterName**, **HostName** and **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

For samples illustrating the **MSBTS\_ReceiveHandler** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

