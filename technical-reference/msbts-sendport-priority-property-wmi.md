---
description: "Learn more about: MSBTS_SendPort.Priority Property (WMI)"
title: MSBTS_SendPort.Priority Property (WMI)
TOCTitle: MSBTS_SendPort.Priority Property (WMI)
ms:assetid: 6f9459d2-d351-4c0e-b215-260c52b28871
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560744(v=BTS.80)
ms:contentKeyID: 51528837
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPort.Priority Property (WMI)

 

Contains the priority of the send port.

*The syntax shown is language neutral.*

## Syntax

```C#
uint32 Priority;  
```

## Remarks

This property is read-write.

The **Priority** property determines the order in which messages are delivered. 1 is the highest priority, 10 is the lowest priority.

For example, if messages 1, 2, and 3 are published, and 3 goes to the port A with a priority setting of 1, while 1 and 2 go to port B with a priority setting of 10, then message 3 will be delivered before messages 1 and 2.

To avoid the prioritization of deliveries, set the **Priority** property to the same value on all ports.

This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPort.Priority** property.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

