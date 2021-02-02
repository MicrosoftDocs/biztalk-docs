---
description: "Learn more about: MSBTS_HostInstance.MgmtDbServerOverride Property (WMI)"
title: MSBTS_HostInstance.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_HostInstance.MgmtDbServerOverride Property (WMI)
ms:assetid: c494f097-9c77-4211-89ec-364f3cbf61da
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547885(v=BTS.80)
ms:contentKeyID: 51531033
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstance.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property has a **Key** qualifier. Along with **Name** and **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

For samples illustrating the **MSBTS\_HostInstance** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

