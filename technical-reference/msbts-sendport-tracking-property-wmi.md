---
description: "Learn more about: MSBTS_SendPort.Tracking Property (WMI)"
title: MSBTS_SendPort.Tracking Property (WMI)
TOCTitle: MSBTS_SendPort.Tracking Property (WMI)
ms:assetid: 4c74d82d-2b5e-47c2-ac21-aa0d3b332ea2
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560036(v=BTS.80)
ms:contentKeyID: 51527876
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: concept-article
---

# MSBTS\_SendPort.Tracking Property (WMI)

 

Contains the tracking configuration for the port.

*The syntax shown is language neutral.*

## Syntax

```C#
uint32 Tracking;  
```

## Return Value

The following table contains the permissible values for this property:

<table>
<thead>
<tr class="header">
<th>Member name</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>AfterReceivePipeline</strong></td>
<td>2</td>
<td>Tracks the entire message immediately after it is processed by the receive pipeline associated with this port.</td>
</tr>
<tr class="even">
<td><strong>AfterSendPipeline</strong></td>
<td>8</td>
<td>Tracks the entire message immediately after it is processed by the send pipeline associated with this port.<br />
<br />
This value is only allowed on two-way send ports.</td>
</tr>
<tr class="odd">
<td><strong>BeforeReceivePipeline</strong></td>
<td>1</td>
<td>Tracks the entire message immediately before it is processed by the receive pipeline associated with this port.</td>
</tr>
<tr class="even">
<td><strong>BeforeSendPipeline</strong></td>
<td>4</td>
<td>Tracks the entire message immediately before it is processed by the send pipeline associated with this port.<br />
<br />
This value is only allowed on two-way send ports.</td>
</tr>
</tbody>
</table>


Note that the integer values must be used in code and script.

## Remarks

This property is read-write.

This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPort.Tracking** property.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

