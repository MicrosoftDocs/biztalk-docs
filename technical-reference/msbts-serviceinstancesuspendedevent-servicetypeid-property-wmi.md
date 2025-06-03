---
description: "Learn more about: MSBTS_ServiceInstanceSuspendedEvent.ServiceTypeID Property (WMI)"
title: MSBTS_ServiceInstanceSuspendedEvent.ServiceTypeID Property (WMI)
TOCTitle: MSBTS_ServiceInstanceSuspendedEvent.ServiceTypeID Property (WMI)
ms:assetid: 84f5f12a-44a1-4b8b-9ab1-e1482c726b5d
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561164(v=BTS.80)
ms:contentKeyID: 51529394
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_ServiceInstanceSuspendedEvent.ServiceTypeID Property (WMI)

 

Contains the GUID of the service type that the service instance referencing this message belongs to. The syntax shown is language neutral.

## Syntax

```C#
  
string ServiceTypeID;  
```

## Remarks

This property is read-only.

For sample code illustrating the **MSBTS\_ServiceInstanceSuspendedEvent** class, see [Listening for a Suspended Event Using WMI](listening-for-a-suspended-event-using-wmi.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

