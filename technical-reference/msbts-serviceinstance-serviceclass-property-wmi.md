---
description: "Learn more about: MSBTS_ServiceInstance.ServiceClass Property (WMI)"
title: MSBTS_ServiceInstance.ServiceClass Property (WMI)
TOCTitle: MSBTS_ServiceInstance.ServiceClass Property (WMI)
ms:assetid: 579015b7-4b61-4b84-a240-fd5544848abd
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560265(v=BTS.80)
ms:contentKeyID: 51528175
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_ServiceInstance.ServiceClass Property (WMI)

 

Contains the name of the service class that corresponds to the message instance. The syntax shown is language neutral.

## Syntax

```C#
  
uint ServiceClass;  
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

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

