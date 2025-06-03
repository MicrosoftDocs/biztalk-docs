---
description: "Learn more about: MSBTS_GroupSetting.LMSThreshold Property (WMI)"
title: MSBTS_GroupSetting.LMSThreshold Property (WMI)
TOCTitle: MSBTS_GroupSetting.LMSThreshold Property (WMI)
ms:assetid: 2f12dc3d-b6a9-4c2e-8d94-0d379ddf01fc
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559435(v=BTS.80)
ms:contentKeyID: 51527145
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_GroupSetting.LMSThreshold Property (WMI)

 

Gets the threshold size, in bytes, for large message support.

The syntax shown is language neutral.

## Syntax

```C#
  
uint32 LMSThreshold;  
```

## Remarks

This property is read-write.

If the in-memory size of a message batch reaches this threshold during processing, the portion of the message batch that has been processed is written to the MessageBox before the remainder of the message batch is processed.

The default value for this property is 1000000.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

