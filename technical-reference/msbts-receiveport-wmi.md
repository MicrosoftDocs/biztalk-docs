---
description: "Learn more about: MSBTS_ReceivePort (WMI)"
title: MSBTS_ReceivePort (WMI)
TOCTitle: MSBTS_ReceivePort (WMI)
ms:assetid: 8500b91b-60be-4a09-a711-b8c840016289
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561166(v=BTS.80)
ms:contentKeyID: 51529396
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceivePort (WMI)

 

Represents an individual receive port defined by BizTalk Server.

## Declaration

```C#
class MSBTS_ReceivePort : MSBTS_Setting  
```

## Members

**MSBTS\_ReceivePort** defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Caption (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/p/?linkid=20246">https://go.microsoft.com/fwlink/p/?LinkID=20246</a>.</td>
</tr>
<tr class="even">
<td>Description (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/p/?linkid=20246">https://go.microsoft.com/fwlink/p/?LinkID=20246</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receiveport-inboundtransforms-property-wmi.md">InboundTransforms</a></td>
<td>Contains a string representation of the maps to apply per inbound document.</td>
</tr>
<tr class="even">
<td><a href="msbts-receiveport-istwoway-property-wmi.md">IsTwoWay</a></td>
<td>Indicates whether this port is a one way or two way port.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receiveport-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-receiveport-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receiveport-name-property-wmi.md">Name</a></td>
<td>Contains the name of the receive port.</td>
</tr>
<tr class="even">
<td><a href="msbts-receiveport-outboundtransforms-property-wmi.md">OutboundTransforms</a></td>
<td>Contains a string representation of the maps to apply per outbound document.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receiveport-primaryreceivelocation-property-wmi.md">PrimaryReceiveLocation</a></td>
<td>Contains the name of the primary receive location for the port.</td>
</tr>
<tr class="even">
<td><a href="msbts-receiveport-sendpipeline-property-wmi.md">SendPipeline</a></td>
<td>Contains a name of the send pipeline for the port.</td>
</tr>
<tr class="odd">
<td>SettingID (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/p/?linkid=20246">https://go.microsoft.com/fwlink/p/?LinkID=20246</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-receiveport-tracking-property-wmi.md">Tracking</a></td>
<td>Contains the tracking configuration for the port.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receiveport-routefailedmessage-property-wmi.md">MSBTS_ReceivePort.RouteFailedMessage Property (WMI)</a></td>
<td>This property controls whether failed messages have to be routed to failed message subscribers.</td>
</tr>
</tbody>
</table>


## Remarks

This class wraps the managed **Microsoft.BizTalk.ExplorerOM.ReceivePort** class.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.
