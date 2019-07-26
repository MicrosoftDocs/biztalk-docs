---
title: MSBTS_HostSetting.ThrottlingSpoolMultiplier Property (WMI)
TOCTitle: MSBTS_HostSetting.ThrottlingSpoolMultiplier Property (WMI)
ms:assetid: a5fb1531-f8cc-4270-ada8-3069ab37acf3
ms:mtpsurl: https://msdn.microsoft.com/library/Gg678633(v=BTS.80)
ms:contentKeyID: 51530244
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
---

# MSBTS\_HostSetting.ThrottlingSpoolMultiplier Property (WMI)

 

Specifies the factor by which the message count in database threshold will be multiplied and then compared against the current record count in the spool table. This determines whether the system should throttle on spool table size.

## Syntax

``` vb
uint32  ThrottlingSpoolMultiplier;  
```

## Remarks

This property is read/write.

If this is set to 0, spool table size is not used as a consideration for determining a throttling condition.

The default value of this property is 10. The maximum value is 1000.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

