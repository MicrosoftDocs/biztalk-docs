---
description: "Learn more about: MSBTS_ReceiveLocation.SrvWinStopDT Property (WMI)"
title: MSBTS_ReceiveLocation.SrvWinStopDT Property (WMI)
TOCTitle: MSBTS_ReceiveLocation.SrvWinStopDT Property (WMI)
ms:assetid: 3961c0d9-7e16-4495-809a-49f37db649f8
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559629(v=BTS.80)
ms:contentKeyID: 51527343
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocation.SrvWinStopDT Property (WMI)

 

Contains the end time of a service window when the receive location should deactivate.

*The syntax shown is language neutral.*

## Syntax

```C#

datetime SrvWinStopDT;
```

## Remarks

Date part of the property is not used.

This property is read-write.

For more information about the format of the datetime value, see the Platform SDK: Windows Management Instrumentation documentation at [https://go.microsoft.com/fwlink/?LinkID=24855](/windows/win32/wmisdk/date-and-time-format).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.