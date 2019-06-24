---
title: MSBTS_ServerHost.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_ServerHost.MgmtDbServerOverride Property (WMI)
ms:assetid: 62979e71-37de-4c0c-991b-34c9e5c1fae3
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560478(v=BTS.80)
ms:contentKeyID: 51528481
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServerHost.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **HostName**, **MgmtDbNameOverride**, and **ServerName**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

For samples illustrating the **MSBTS\_ServerHost** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

