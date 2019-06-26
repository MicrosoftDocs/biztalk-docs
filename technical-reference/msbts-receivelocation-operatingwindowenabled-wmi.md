---
title: MSBTS_ReceiveLocation.OperatingWindowEnabled (WMI)
TOCTitle: MSBTS_ReceiveLocation.OperatingWindowEnabled (WMI)
ms:assetid: a4c5f567-be5a-4154-94c0-99e5b92ea778
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577868(v=BTS.80)
ms:contentKeyID: 51530207
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocation.OperatingWindowEnabled (WMI)

 

Enables or disables a service window, which is defined by the **SrvWinStartDT** and **SrvWinStopDT** properties.

*The syntax shown is language neutral.*

## Syntax

```C#
  
boolean ServiceWindowEnabled = FALSE;  
```

## Remarks

This property is read-write.

The default value for this property is **FALSE**.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

