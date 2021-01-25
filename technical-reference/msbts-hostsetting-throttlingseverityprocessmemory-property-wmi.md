---
description: "Learn more about: MSBTS_HostSetting.ThrottlingSeverityProcessMemory Property (WMI)"
title: MSBTS_HostSetting.ThrottlingSeverityProcessMemory Property (WMI)
TOCTitle: MSBTS_HostSetting.ThrottlingSeverityProcessMemory Property (WMI)
ms:assetid: d3871300-a44f-49c3-91bf-f8e3a1cb0413
ms:mtpsurl: https://msdn.microsoft.com/library/Gg678639(v=BTS.80)
ms:contentKeyID: 51531572
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostSetting.ThrottlingSeverityProcessMemory Property (WMI)

 

Controls the severity of a process memory triggered throttling condition. This is specified in percentage value and this parameter sets the severity of a throttling condition caused when the process memory usage threshold is exceeded.

The syntax shown is language neutral.

## Syntax

```C#
uint32  ThrottlingSeverityProcessMemory;  
```

## Remarks

This property is read/write.

The default value of this property is 500.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

