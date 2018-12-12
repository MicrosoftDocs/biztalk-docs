---
title: MSBTS_GroupSetting.PerfCounterCacheRefreshInterval Property (WMI)
TOCTitle: MSBTS_GroupSetting.PerfCounterCacheRefreshInterval Property (WMI)
ms:assetid: d984a408-d4a8-498e-ab8c-71a08be87e1b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Gg678644(v=BTS.80)
ms:contentKeyID: 51531743
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_GroupSetting.PerfCounterCacheRefreshInterval Property (WMI)

 

This property indicates the interval at which performance counters are refreshed.

The syntax shown is language neutral.

## Syntax

```C#
  
uint32 PerfCounterCacheRefreshInterval;  
```

## Remarks

This property is read-write.

If the in-memory size of a message batch reaches this threshold during processing, the portion of the message batch that has been processed is written to the MessageBox before the remainder of the message batch is processed.

The range for this property is 1 to 43200.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

