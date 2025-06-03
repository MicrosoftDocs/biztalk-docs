---
description: "Learn more about: MSBTS_HostSetting.DehydrationBehavior Property (WMI)"
title: MSBTS_HostSetting.DehydrationBehavior Property (WMI)
TOCTitle: MSBTS_HostSetting.DehydrationBehavior Property (WMI)
ms:assetid: 1b672a19-0080-4025-8b6d-80e4a6056f40
ms:mtpsurl: https://msdn.microsoft.com/library/Gg678622(v=BTS.80)
ms:contentKeyID: 51526569
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_HostSetting.DehydrationBehavior Property (WMI)

 

This property controls the dehydration behavior of the orchestration (XLANG) engine. Other XLANG settings should only be editable if the value is Custom.

## Syntax

```C#
uint32  DehydrationBehavior;  
```

## Property Value/Return Value

Values: 0 = Always; 1 = Never; 2 = Custom.

## Remarks

This property is read/write.

The default value of this property is 2 (Custom).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

