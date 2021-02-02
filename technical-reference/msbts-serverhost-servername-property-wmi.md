---
description: "Learn more about: MSBTS_ServerHost.ServerName Property (WMI)"
title: MSBTS_ServerHost.ServerName Property (WMI)
TOCTitle: MSBTS_ServerHost.ServerName Property (WMI)
ms:assetid: 53c15dc0-3386-42c9-9451-65954f1356ac
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560188(v=BTS.80)
ms:contentKeyID: 51528080
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServerHost.ServerName Property (WMI)

 

Contains the name of the server.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string ServerName;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **HostName**, **MgmtDbNameOverride**, and **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 63 characters.

For samples illustrating the **MSBTS\_ServerHost** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

