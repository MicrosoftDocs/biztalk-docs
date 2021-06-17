---
description: "Learn more about: MSBTS_SendPort.PTFromTime Property (WMI)"
title: MSBTS_SendPort.PTFromTime Property (WMI)
TOCTitle: MSBTS_SendPort.PTFromTime Property (WMI)
ms:assetid: 8d7d19b0-7e33-4d81-a689-5568854a1aba
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561319(v=BTS.80)
ms:contentKeyID: 51529612
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPort.PTFromTime Property (WMI)

 

Contains the start time of the service window of the primary transport for the port.

*The syntax shown is language neutral.*

## Syntax

```C#

datetime PTFromTime;
```

## Remarks

This property is read-write.

For more information about the format of the datetime value, see the Platform SDK: Windows Management Instrumentation documentation at [https://go.microsoft.com/fwlink/?LinkID=24855](/windows/win32/wmisdk/date-and-time-format).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.