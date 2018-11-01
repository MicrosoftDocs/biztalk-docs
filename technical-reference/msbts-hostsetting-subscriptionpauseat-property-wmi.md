---
title: MSBTS_HostSetting.SubscriptionPauseAt Property (WMI)
TOCTitle: MSBTS_HostSetting.SubscriptionPauseAt Property (WMI)
ms:assetid: caa006f1-e5ac-40b9-9558-c4eb2f87ea29
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Gg678638(v=BTS.80)
ms:contentKeyID: 51531315
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostSetting.SubscriptionPauseAt Property (WMI)

 

Specifies the number of messages a subscription must have waiting to be consumed before message delivery to that subscription instance is paused.

The syntax shown is language neutral.

## Syntax

``` 
uint32  SubscriptionPauseAt;  
```

## Remarks

This property is read/write.

The default value of this property is 0.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

