---
description: "Learn more about: MSBTS_AdapterSetting.DefaultOutboundCfg Property (WMI)"
title: MSBTS_AdapterSetting.DefaultOutboundCfg Property (WMI)
TOCTitle: MSBTS_AdapterSetting.DefaultOutboundCfg Property (WMI)
ms:assetid: 63ccfec4-2e9e-4ed0-b041-677ac8425da5
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560500(v=BTS.80)
ms:contentKeyID: 51528499
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_AdapterSetting.DefaultOutboundCfg Property (WMI)

 

Gets a default outbound configuration for the adapter.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string DefaultOutboundCfg;  
```

## Remarks

This property is read-only.

The maximum length for this property is 1024 characters.

This configuration is used when a new [MSBTS\_SendHandler](msbts-sendhandler-wmi.md) instance is created.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

