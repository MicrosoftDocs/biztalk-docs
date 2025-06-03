---
description: "Learn more about: MSBTS_ReceiveHandler.AdapterName Property (WMI)"
title: MSBTS_ReceiveHandler.AdapterName Property (WMI)
TOCTitle: MSBTS_ReceiveHandler.AdapterName Property (WMI)
ms:assetid: 4e2c0948-1358-488e-a137-dcca96976eb8
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560071(v=BTS.80)
ms:contentKeyID: 51527922
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_ReceiveHandler.AdapterName Property (WMI)

 

Contains the name of the adapter.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string AdapterName;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

This property has a Key qualifier. Along with **HostName**, **MgmtDbServerOverride**, and **MgmtDbNameOverride**, this key forms a compound key for the class.

The maximum length for this property is 256 characters.

For samples illustrating the **MSBTS\_ReceiveHandler** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

