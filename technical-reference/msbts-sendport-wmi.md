---
description: "Learn more about: MSBTS_SendPort (WMI)"
title: MSBTS_SendPort (WMI)
TOCTitle: MSBTS_SendPort (WMI)
ms:assetid: 3f3767e1-4590-41b2-8ee3-02eac6ea8c5c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559751(v=BTS.80)
ms:contentKeyID: 51527565
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPort (WMI)

 

Represents an individual send port defined by BizTalk Server.


> [!WARNING]
> <P>Certificates must be installed on the box for the MSBTS_SendPort class to work. The only way to create send ports without certificates is to use the <A href="/previous-versions/">Microsoft.BizTalk.ExplorerOM</A> APIs.</P>



## Declaration

```C#
class MSBTS_SendPort : MSBTS_Setting  
```

## Members

**MSBTS\_SendPort** defines the following properties:

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
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-setting">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="even">
<td>Description (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-setting">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-encryptioncert-property-wmi.md">EncryptionCert</a></td>
<td>Specifies the certificate to use for outbound encryption.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-filter-property-wmi.md">Filter</a></td>
<td>Contains textual representation of the filter.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-inboundtransforms-property-wmi.md">InboundTransforms</a></td>
<td>Contains a string representation of the maps to apply per inbound document.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-isdynamic-property-wmi.md">IsDynamic</a></td>
<td>Indicates whether this port is a dynamic or static.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-istwoway-property-wmi.md">IsTwoWay</a></td>
<td>Indicates whether this port is a one way or two way port.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-name-property-wmi.md">Name</a></td>
<td>Contains the name of the send port.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-outboundtransforms-property-wmi.md">OutboundTransforms</a></td>
<td>Contains a string representation of the maps to apply per outbound document.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-priority-property-wmi.md">Priority</a></td>
<td>Contains the priority of the send port.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-ptaddress-property-wmi.md">PTAddress</a></td>
<td>Contains the URL of primary transport for the port.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-ptcustomcfg-property-wmi.md">PTCustomCfg</a></td>
<td>Contains transport type data for the primary transport of the port.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-ptfromtime-property-wmi.md">PTFromTime</a></td>
<td>Contains the start time of the service window of the primary transport for the port.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-ptordereddelivery-property-wmi.md">PTOrderedDelivery</a></td>
<td>Determines whether the primary transport for the port supports ordered delivery.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-ptretrycount-property-wmi.md">PTRetryCount</a></td>
<td>Contains the number of retries available for the primary transport of the port.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-ptretryinterval-property-wmi.md">PTRetryInterval</a></td>
<td>Contains the retry interval for the primary transport of the port.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-ptservicewindowenabled-property-wmi.md">PTServiceWindowEnabled</a></td>
<td>Determines whether a service window of the primary transport for the port is enabled.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-pttotime-property-wmi.md">PTToTime</a></td>
<td>Contains the end time of the service window of the primary transport for the port.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-pttransporttype-property-wmi.md">PTTransportType</a></td>
<td>Contains the transport type of the primary transport for the port.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-receivepipeline-property-wmi.md">ReceivePipeline</a></td>
<td>Contains a name of the receive pipeline for the port.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-sendpipeline-property-wmi.md">SendPipeline</a></td>
<td>Contains a name of the send pipeline for the port.</td>
</tr>
<tr class="even">
<td>SettingID (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-setting">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-status-property-wmi.md">Status</a></td>
<td>Displays the current status of the port.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-staddress-property-wmi.md">STAddress</a></td>
<td>Contains the URL of secondary transport for the port.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-stcustomcfg-property-wmi.md">STCustomCfg</a></td>
<td>Contains transport type data for the secondary transport of the port.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-stfromtime-property-wmi.md">STFromTime</a></td>
<td>Contains the start time of the service window of the secondary transport for the port.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-stordereddelivery-property-wmi.md">STOrderedDelivery</a></td>
<td>Determines whether the secondary transport for the port supports ordered delivery.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-stretrycount-property-wmi.md">STRetryCount</a></td>
<td>Contains the number of retries available for the secondary transport of the port.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-stretryinterval-property-wmi.md">STRetryInterval</a></td>
<td>Contains the retry interval for the secondary transport of the port.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-stservicewindowenabled-property-wmi.md">STServiceWindowEnabled</a></td>
<td>Determines whether a service window of the secondary transport for the port is enabled.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-sttotime-property-wmi.md">STToTime</a></td>
<td>Contains the end time of the service window of the secondary transport for the port.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-sttransporttype-property-wmi.md">STTransportType</a></td>
<td>Contains the transport type of the secondary transport for the port.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-tracking-property-wmi.md">Tracking</a></td>
<td>Contains the tracking configuration for the port.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-ordereddelivery-property-wmi.md">MSBTS_SendPort.OrderedDelivery Property (WMI)</a></td>
<td>This property determines whether the port should send messages in an ordered manner.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-stopsendingonfailure-property-wmi.md">StopSendingOnFailure</a></td>
<td>This property controls how EPM handles failures for order delivery enabled send port's primary transport.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-routefailedmessage-property-wmi.md">MSBTS_SendPort.RouteFailedMessage Property (WMI)</a></td>
<td>This property controls whether failed messages have to be routed to failed message subscribers.</td>
</tr>
</tbody>
</table>


**MSBTS\_SendPort** defines the following methods:

<table>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-sendport-enlist-method-wmi.md">Enlist</a></td>
<td>Enlists the send port.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-start-method-wmi.md">Start</a></td>
<td>Starts the send port.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendport-stop-method-wmi.md">Stop</a></td>
<td>Stops the send port.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-unenlist-method-wmi.md">UnEnlist</a></td>
<td>Unenlists the send port.</td>
</tr>
</tbody>
</table>


## Remarks

If a send port or receive location is updated using the BizTalk Explorer object model or a WMI script, the Receive Port Properties and Send Port Properties property pages in BizTalk Explorer will display an incorrect Address (URI). The Address (URI) used internally is the Address (URI) set by the script, so the script works as expected. To update the property pages to display the correct Address (URI), update the Address (URI) field in BizTalk Explorer with the new value.

This class wraps the managed **Microsoft.BizTalk.ExplorerOM.ReceivePort** class. For more information about this class, see **InboundTransforms**.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.