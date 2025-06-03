---
description: "Learn more about: MSBTS_HostSetting.TimeBasedMaxThreshold Property (WMI)"
title: MSBTS_HostSetting.TimeBasedMaxThreshold Property (WMI)
TOCTitle: MSBTS_HostSetting.TimeBasedMaxThreshold Property (WMI)
ms:assetid: d49968f4-81c9-4ef7-aa08-a58381d80d24
ms:mtpsurl: https://msdn.microsoft.com/library/Gg678640(v=BTS.80)
ms:contentKeyID: 51531487
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_HostSetting.TimeBasedMaxThreshold Property (WMI)

 

This property is the maximum wait time, in seconds, an orchestration instance can block before being dehydrated.

The syntax shown is language neutral.

## Syntax

```C#
uint32  TimeBasedMaxThreshold;  
```

## Remarks

This property is read/write.

The default value of this property is 1800.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

