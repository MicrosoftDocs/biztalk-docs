---
description: "Learn more about: MSBTS_ServiceInstanceSuspendedEvent.ServiceStatus Property (WMI)"
title: MSBTS_ServiceInstanceSuspendedEvent.ServiceStatus Property (WMI)
TOCTitle: MSBTS_ServiceInstanceSuspendedEvent.ServiceStatus Property (WMI)
ms:assetid: e3f562d8-c254-4244-bc9e-992a223651dd
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561592(v=BTS.80)
ms:contentKeyID: 51532967
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_ServiceInstanceSuspendedEvent.ServiceStatus Property (WMI)

 

Contains the state of the service instance. The syntax shown is language neutral.

## Syntax

```C#
  
Uint32 ServiceStatus;  
```

## Remarks

This property is read-only.

The following table contains the permissible values for this property:

<table>
<thead>
<tr class="header">
<th>Description</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Suspended (resumable)</td>
<td>1</td>
</tr>
<tr class="even">
<td>Suspended (not resumable)</td>
<td>2</td>
</tr>
<tr class="odd">
<td>Completed with discarded messages</td>
<td>4</td>
</tr>
</tbody>
</table>


Note that the integer values must be used in code and script.

For sample code illustrating the **MSBTS\_ServiceInstanceSuspendedEvent** class, see [Listening for a Suspended Event Using WMI](listening-for-a-suspended-event-using-wmi.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

