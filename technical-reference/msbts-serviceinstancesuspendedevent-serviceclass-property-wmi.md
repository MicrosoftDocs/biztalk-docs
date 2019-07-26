---
title: MSBTS_ServiceInstanceSuspendedEvent.ServiceClass Property (WMI)
TOCTitle: MSBTS_ServiceInstanceSuspendedEvent.ServiceClass Property (WMI)
ms:assetid: 3608e63f-fc11-4f2b-8338-37e1dd772711
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559570(v=BTS.80)
ms:contentKeyID: 51527325
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServiceInstanceSuspendedEvent.ServiceClass Property (WMI)

 

Contains the class of the service instance to which this message belongs. The syntax shown is language neutral.

## Syntax

```C#
  
uint32 ServiceClass;  
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
<td>Orchestration</td>
<td>1</td>
</tr>
<tr class="even">
<td>Tracking</td>
<td>2</td>
</tr>
<tr class="odd">
<td>Messaging</td>
<td>4</td>
</tr>
<tr class="even">
<td>MSMQT</td>
<td>8</td>
</tr>
<tr class="odd">
<td>Other</td>
<td>16</td>
</tr>
<tr class="even">
<td>Isolated adapter</td>
<td>32</td>
</tr>
<tr class="odd">
<td>Routing failure report</td>
<td>64</td>
</tr>
</tbody>
</table>


Note that the integer values must be used in code and script.

For sample code illustrating the **MSBTS\_ServiceInstanceSuspendedEvent** class, see [Listening for a Suspended Event Using WMI](listening-for-a-suspended-event-using-wmi.md).

