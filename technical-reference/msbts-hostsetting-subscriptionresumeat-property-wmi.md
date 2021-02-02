---
description: "Learn more about: MSBTS_HostSetting.SubscriptionResumeAt Property (WMI)"
title: MSBTS_HostSetting.SubscriptionResumeAt Property (WMI)
TOCTitle: MSBTS_HostSetting.SubscriptionResumeAt Property (WMI)
ms:assetid: ca4c24c3-4a9c-436b-96a2-2cfb5f4e311a
ms:mtpsurl: https://msdn.microsoft.com/library/Gg678637(v=BTS.80)
ms:contentKeyID: 51531178
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostSetting.SubscriptionResumeAt Property (WMI)

 

Specifies the number of remaining unconsumed messages at which message delivery is resumed to a subscription instance that has been paused because of a PauseAt setting.

The syntax shown is language neutral.

## Syntax

```C#
uint32  SubscriptionResumeAt;  
```

## Remarks

This property is read/write.

The default value of this property is 0.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

