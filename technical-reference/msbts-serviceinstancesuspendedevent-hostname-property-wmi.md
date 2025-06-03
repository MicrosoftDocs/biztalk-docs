---
description: "Learn more about: MSBTS_ServiceInstanceSuspendedEvent.HostName Property (WMI)"
title: MSBTS_ServiceInstanceSuspendedEvent.HostName Property (WMI)
TOCTitle: MSBTS_ServiceInstanceSuspendedEvent.HostName Property (WMI)
ms:assetid: 4b1ba4f8-408d-4170-a328-2a2e37ccc135
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560012(v=BTS.80)
ms:contentKeyID: 51527846
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_ServiceInstanceSuspendedEvent.HostName Property (WMI)

 

Contains the name of the BizTalk Host that corresponds to this queue. The syntax shown is language neutral.

## Syntax

```C#
  
string HostName;  
```

## Remarks

This property is read-only.

The maximum length for this property is 80 characters.

For sample code illustrating the **MSBTS\_ServiceInstanceSuspendedEvent** class, see [Listening for a Suspended Event Using WMI](listening-for-a-suspended-event-using-wmi.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

