---
title: MSBTS_AdapterSetting.Name Property (WMI)
TOCTitle: MSBTS_AdapterSetting.Name Property (WMI)
ms:assetid: 43264ec1-652f-4c2f-b4a8-70f9f42fba13
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559817(v=BTS.80)
ms:contentKeyID: 51527592
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_AdapterSetting.Name Property (WMI)

 

Gets the name of the adapter.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string Name;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

This property has a **Key** qualifier. Along with [MgmtDbNameOverride](msbts-adaptersetting-mgmtdbnameoverride-property-wmi.md) and [MgmtDbServerOverride](msbts-adaptersetting-mgmtdbserveroverride-property-wmi.md), this key forms a compound key for the class.

The maximum length for this property is 256 characters

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

