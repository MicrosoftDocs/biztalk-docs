---
title: MSBTS_HostSetting.ThrottlingLimitToTriggerGC Property (WMI)
TOCTitle: MSBTS_HostSetting.ThrottlingLimitToTriggerGC Property (WMI)
ms:assetid: d677733d-a88b-4acf-a325-b099e0224de5
ms:mtpsurl: https://msdn.microsoft.com/library/Gg678642(v=BTS.80)
ms:contentKeyID: 51531669
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
---

# MSBTS\_HostSetting.ThrottlingLimitToTriggerGC Property (WMI)

 

Specifies the percentage of the process memory consumption threshold at which a .NET Framework garbage collection (GC) will be triggered.

## Syntax

``` vb
uint32  ThrottlingLimitToTriggerGC;  
```

## Remarks

This property is read/write.

The default value of this property is 80. The minimum value is 50 and the maximum value is 100.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

