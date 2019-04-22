---
title: MSBTS_HostSetting.DeliveryQueueSize Property (WMI)
TOCTitle: MSBTS_HostSetting.DeliveryQueueSize Property (WMI)
ms:assetid: 9be7f63e-9521-4d39-8c74-810a9b157805
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577556(v=BTS.80)
ms:contentKeyID: 51529991
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostSetting.DeliveryQueueSize Property (WMI)

 

This property represents the size of the in-memory queue. This queue serves as a temporary placeholder for delivering messages.

## Syntax

```C#
  
uint32 DeliveryQueueSize;  
```

## Remarks

The default value for this parameter is 100.

This property is read/write.

The syntax shown is language neutral.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

