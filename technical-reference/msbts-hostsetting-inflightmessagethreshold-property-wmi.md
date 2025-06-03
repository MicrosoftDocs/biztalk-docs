---
description: "Learn more about: MSBTS_HostSetting.InflightMessageThreshold Property (WMI)"
title: MSBTS_HostSetting.InflightMessageThreshold Property (WMI)
TOCTitle: MSBTS_HostSetting.InflightMessageThreshold Property (WMI)
ms:assetid: bace1a98-8c17-4613-bc42-1712e02fbf3d
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578331(v=BTS.80)
ms:contentKeyID: 51530808
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_HostSetting.InflightMessageThreshold Property (WMI)

 

This property represents the maximum number of in-memory in-flight messages allowed before throttling Message Delivery begins.

## Syntax

```C#
  
uint32InflightMessageThreshold;  
```

## Remarks

The default value for this parameter is 1000.

This property is read/write.

The syntax shown is language neutral.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

