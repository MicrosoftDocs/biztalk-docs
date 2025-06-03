---
description: "Learn more about: MSBTS_HostSetting.MessagePublishMaximumDelay Property (WMI)"
title: MSBTS_HostSetting.MessagePublishMaximumDelay Property (WMI)
TOCTitle: MSBTS_HostSetting.MessagePublishMaximumDelay Property (WMI)
ms:assetid: 5b853465-446d-4a44-bad4-a5652ef6a436
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560347(v=BTS.80)
ms:contentKeyID: 51528286
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_HostSetting.MessagePublishMaximumDelay Property (WMI)

 

The maximum Delay (in milliseconds) imposed for Message Publishing Throttling. Zero indicates that Message Publishing Throttling is disabled.

## Syntax

```C#
  
uint32MessagePublishMaximumDelay;  
```

## Remarks

The default value for this parameter is 1000000.

This property is read/write.

The syntax shown is language neutral.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

