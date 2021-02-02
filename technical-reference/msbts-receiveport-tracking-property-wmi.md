---
description: "Learn more about: MSBTS_ReceivePort.Tracking Property (WMI)"
title: MSBTS_ReceivePort.Tracking Property (WMI)
TOCTitle: MSBTS_ReceivePort.Tracking Property (WMI)
ms:assetid: b96f44e5-f1fc-4cca-b467-fc1119079639
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578309(v=BTS.80)
ms:contentKeyID: 51530788
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceivePort.Tracking Property (WMI)

 

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

This property wraps the managed **Microsoft.BizTalk.ExplorerOM.ReceivePort.Tracking** property.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

