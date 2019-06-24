---
title: MSBTS_ServiceInstanceSuspendedEvent.ServiceClassID Property (WMI)
TOCTitle: MSBTS_ServiceInstanceSuspendedEvent.ServiceClassID Property (WMI)
ms:assetid: a078d096-50f7-4b43-ad97-7627eaaa0025
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577669(v=BTS.80)
ms:contentKeyID: 51530072
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServiceInstanceSuspendedEvent.ServiceClassID Property (WMI)

 

Contains the GUID of the service class that the service instance referencing this message belongs to. The syntax shown is language neutral.

## Syntax

```C#
  
string ServiceClassID;  
```

## Remarks

This property is read-only.

For sample code illustrating the **MSBTS\_ServiceInstanceSuspendedEvent** class, see [Listening for a Suspended Event Using WMI](listening-for-a-suspended-event-using-wmi.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

