---
description: "Learn more about: MSBTS_SendPort.STFromTime Property (WMI)"
title: MSBTS_SendPort.STFromTime Property (WMI)
TOCTitle: MSBTS_SendPort.STFromTime Property (WMI)
ms:assetid: d3cbe6a3-2556-4aa4-87a6-fb02e8ab5b29
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578583(v=BTS.80)
ms:contentKeyID: 51531580
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPort.STFromTime Property (WMI)

 

Contains the start time of the service window of the secondary transport for the port.

*The syntax shown is language neutral.*

## Syntax

```C#

datetime STFromTime;
```

## Remarks

This property is read-write.

For more information about the format of the datetime value, see the Platform SDK: Windows Management Instrumentation documentation at [https://go.microsoft.com/fwlink/?LinkID=24855](/windows/win32/wmisdk/date-and-time-format).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.