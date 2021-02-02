---
description: "Learn more about: MSBTS_HostSetting.ThrottlingSeverityDatabaseSize Property (WMI)"
title: MSBTS_HostSetting.ThrottlingSeverityDatabaseSize Property (WMI)
TOCTitle: MSBTS_HostSetting.ThrottlingSeverityDatabaseSize Property (WMI)
ms:assetid: ff74a03c-fd19-4148-9f65-e65ef7f80213
ms:mtpsurl: https://msdn.microsoft.com/library/Gg678645(v=BTS.80)
ms:contentKeyID: 51533830
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostSetting.ThrottlingSeverityDatabaseSize Property (WMI)

 

This property controls the severity of a database sized triggered throttling condition. This is specified in percentage value and this parameter sets the severity of a throttling condition caused when the message count in database threshold is exceeded.

The syntax shown is language neutral.

## Syntax

```C#
uint32  ThrottlingSeverityDatabaseSize;  
```

## Remarks

This property is read/write.

The default value of this property is 1.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

