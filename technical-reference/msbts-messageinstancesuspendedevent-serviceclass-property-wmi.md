---
title: MSBTS_MessageInstanceSuspendedEvent.ServiceClass Property (WMI)
TOCTitle: MSBTS_MessageInstanceSuspendedEvent.ServiceClass Property (WMI)
ms:assetid: 8464a83d-d1cc-4f14-9c75-900166ebe2bd
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561151(v=BTS.80)
ms:contentKeyID: 51529381
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_MessageInstanceSuspendedEvent.ServiceClass Property (WMI)

 

Contains the class of the service instance to which this message belongs.

*The syntax shown is language neutral.*

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
<td>Other</td>
<td>16</td>
</tr>
<tr class="odd">
<td>Isolated adapter</td>
<td>32</td>
</tr>
<tr class="even">
<td>Routing failure report</td>
<td>64</td>
</tr>
</tbody>
</table>


Note that the integer values must be used in code and script.

