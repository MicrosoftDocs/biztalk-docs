---
description: "Learn more about: MSBTS_HostSetting.ThrottlingSeverityInflightMessage Property (WMI)"
title: MSBTS_HostSetting.ThrottlingSeverityInflightMessage Property (WMI)
TOCTitle: MSBTS_HostSetting.ThrottlingSeverityInflightMessage Property (WMI)
ms:assetid: 258463ae-1225-476c-a6e5-bffd3272455c
ms:mtpsurl: https://msdn.microsoft.com/library/Gg678624(v=BTS.80)
ms:contentKeyID: 51526838
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_HostSetting.ThrottlingSeverityInflightMessage Property (WMI)

 

This property controls the reaction time of throttling when the in-process size exceeds the threshold. This is specified in percentage value and this parameter sets the severity of a throttling condition caused when the in-process messages per CPU threshold is exceeded.

The syntax shown is language neutral.

## Syntax

```C#
uint32  ThrottlingSeverityInflightMessage;  
```

## Remarks

This property is read/write.

The default value of this property is 75.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

