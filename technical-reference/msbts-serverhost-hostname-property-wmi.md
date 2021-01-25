---
description: "Learn more about: MSBTS_ServerHost.HostName Property (WMI)"
title: MSBTS_ServerHost.HostName Property (WMI)
TOCTitle: MSBTS_ServerHost.HostName Property (WMI)
ms:assetid: 3f1b11db-b823-4cf4-aa29-dbb95648ce1d
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559747(v=BTS.80)
ms:contentKeyID: 51527561
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServerHost.HostName Property (WMI)

 

Contains the name of the host.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string HostName;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **ServerName**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

For samples illustrating the **MSBTS\_ServerHost** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

