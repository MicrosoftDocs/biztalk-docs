---
title: MSBTS_HostSetting.DBSessionThreshold Property (WMI)
TOCTitle: MSBTS_HostSetting.DBSessionThreshold Property (WMI)
ms:assetid: 32725bbb-b78b-42f7-bde1-fb06a668481a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559497(v=BTS.80)
ms:contentKeyID: 51527229
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostSetting.DBSessionThreshold Property (WMI)

 

This parameter represents the maximum number of DB Sessions (per CPU) allowed before throttling begins.

## Syntax

```C#
  
uint32DBSessionThreshold;  
```

## Remarks

The default value for this parameter is 0.

This property is read/write.

The syntax shown is language neutral.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

