---
title: MSBTS_HostSetting.ThreadThreshold Property (WMI)
TOCTitle: MSBTS_HostSetting.ThreadThreshold Property (WMI)
ms:assetid: 37b07342-3d3b-4abb-adae-7b4ccb6309f4
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559604(v=BTS.80)
ms:contentKeyID: 51527307
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostSetting.ThreadThreshold Property (WMI)

 

This property lists the maximum number of threads in the process (per CPU) allowed before throttling begins.

## Syntax

``` 
  
uint32ThreadThreshold;  
```

## Remarks

The default value for this parameter is 0.

This property is read/write.

The syntax shown is language neutral.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

