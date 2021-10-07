---
description: "Learn more about: MSBTS_ReceiveLocation.SrvWinStartDT Property (WMI)"
title: MSBTS_ReceiveLocation.SrvWinStartDT Property (WMI)
TOCTitle: MSBTS_ReceiveLocation.SrvWinStartDT Property (WMI)
ms:assetid: 3057540b-8c4f-4daa-802b-9357e56bbdda
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559461(v=BTS.80)
ms:contentKeyID: 51527109
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocation.SrvWinStartDT Property (WMI)

 

Contains the start time of a service window when the receive location should activate.

*The syntax shown is language neutral.*

## Syntax

```C#

datetime SrvWinStartDT;
```

## Remarks

Date part of the property is not used.

This property is read-write.

For more information about the format of the datetime value, see the Platform SDK: Windows Management Instrumentation documentation at [https://go.microsoft.com/fwlink/?LinkID=24855](/windows/win32/wmisdk/date-and-time-format).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.