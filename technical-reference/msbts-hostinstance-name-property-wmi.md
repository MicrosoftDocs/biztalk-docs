---
title: MSBTS_HostInstance.Name Property (WMI)
TOCTitle: MSBTS_HostInstance.Name Property (WMI)
ms:assetid: a9536d39-7837-48b0-b1e6-e4ab832dcc5f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577954(v=BTS.80)
ms:contentKeyID: 51530372
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstance.Name Property (WMI)

 

Contains the name of the host instance.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string Name;  
```

## Remarks

This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 128 characters.

For samples illustrating the **MSBTS\_HostInstance** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

