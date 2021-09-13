---
description: "Learn more about: MSBTS_GroupSetting.ReceiverFaultToleranceRetryInterval Property (WMI)"
title: MSBTS_GroupSetting.ReceiverFaultToleranceRetryInterval Property (WMI)
TOCTitle: MSBTS_GroupSetting.ReceiverFaultToleranceRetryInterval Property (WMI)
ms.date: 09/13/2021
---

# MSBTS\_GroupSetting.ReceiverFaultToleranceRetryInterval Property (WMI)

 

Gets or sets how often the server attempts to recover receive location from failures when receive location fault tolerance is enabled, in seconds.

Available BizTalk Server 2020 onwards. Please see how to [enable receive location fault tolerance](../how-to-enable-receive-location-fault-tolerance.md) for further details.

The syntax shown is language neutral.

## Syntax

```C#
  
uint32 ReceiverFaultToleranceRetryInterval;  
```

## Remarks

This property is read-write.

The default value for this property is 60.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.
