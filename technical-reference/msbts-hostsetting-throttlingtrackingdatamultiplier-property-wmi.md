---
title: MSBTS_HostSetting.ThrottlingTrackingDataMultiplier Property (WMI)
TOCTitle: MSBTS_HostSetting.ThrottlingTrackingDataMultiplier Property (WMI)
ms:assetid: 2362aaa6-7e9e-4587-bdeb-c1019563e0c3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Gg678623(v=BTS.80)
ms:contentKeyID: 51526802
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
---

# MSBTS\_HostSetting.ThrottlingTrackingDataMultiplier Property (WMI)

 

Specifies the factor by which the message count in database threshold will be multiplied and then compared against the current record count in the tracking table. This determines whether the system should throttle on tracking table size.

## Syntax

``` vb
uint32  ThrottlingTrackingDataMultiplier;  
```

## Remarks

This property is read/write.

If this is set to 0, tracking table size is not used as a consideration for determining a throttling condition.

The default value of this property is 10. The maximum value is 1000.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

