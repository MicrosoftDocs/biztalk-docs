---
description: "Learn more about: MSBTS_ServiceInstance.PendingOperation Property (WMI)"
title: MSBTS_ServiceInstance.PendingOperation Property (WMI)
TOCTitle: MSBTS_ServiceInstance.PendingOperation Property (WMI)
ms:assetid: 9acee351-b855-49c0-9adc-d2eac20d3ef6
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577534(v=BTS.80)
ms:contentKeyID: 51529902
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_ServiceInstance.PendingOperation Property (WMI)

 

Contains the type of a pending operations (if any) for this service instance. The syntax shown is language neutral.

## Syntax

```C#
  
uint32 PendingOperation;  
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
<td>No operation</td>
<td>1</td>
</tr>
<tr class="even">
<td>Suspend</td>
<td>2</td>
</tr>
<tr class="odd">
<td>Terminate</td>
<td>4</td>
</tr>
<tr class="even">
<td>Resume</td>
<td>8</td>
</tr>
</tbody>
</table>


Note that the integer values must be used in code and script.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

