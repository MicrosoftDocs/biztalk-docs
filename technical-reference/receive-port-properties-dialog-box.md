---
description: "Learn more about: Receive Port Properties Dialog Box"
title: Receive Port Properties Dialog Box
TOCTitle: Receive Port Properties Dialog Box
ms:assetid: ad315dc4-2894-4bcf-84d9-e2827b328f7c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578044(v=BTS.80)
ms:contentKeyID: 51530492
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.receiveport.properties
---

# Receive Port Properties Dialog Box

Use the **Receive Port Properties** window to view the properties of an existing receive port and to create and configure a new receive port.

## General Tab

Specific properties that are applicable only to two-way ports are hidden for one-way ports.

The following table lists the UIElements in the **General** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Name</strong></td>
<td>Type the name of the port.</td>
</tr>
<tr class="even">
<td><strong>Port type</strong></td>
<td>Displays the port type. Receive ports may be one-way or request-response. You select the port type when you create the port; if an existing port is the wrong type for your purposes, you must re-create the port.</td>
</tr>
<tr class="odd">
<td><strong>Authentication - No Authentication</strong></td>
<td>Click this option to disable authentication when party resolution authentication is configured.</td>
</tr>
<tr class="even">
<td><strong>Authentication - Drop messages if authentication fails</strong></td>
<td>Click this option to enable authentication, but drop unauthenticated messages. This option takes effect when party resolution authentication is configured.</td>
</tr>
<tr class="odd">
<td><strong>Authentication - Keep messages if authentication fails</strong></td>
<td>Click this option to enable authentication and keep unauthenticated messages. Messages are kept in the suspended queue. This option takes effect when party resolution authentication is configured.</td>
</tr>
<tr class="even">
<td><strong>Enable routing for failed messages</strong></td>
<td>Select this check box to attempt to route any message that fails processing to a subscribing application (such as another receive port or orchestration schedule). Clear the check box to suspend failed messages and generate a negative acknowledgment (NACK). The default value is cleared.</td>
</tr>
<tr class="odd">
<td><strong>Description</strong></td>
<td>Type any text that will help you distinguish this receive port from others. The maximum number of characters allowed is 256.</td>
</tr>
</tbody>
</table>

## Receive Locations Tab

The following table lists the UIElements in the **Receive Locations** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>New</strong></td>
<td>Click to open the <strong>Receive Location Properties</strong> page and set up a new receive location.</td>
</tr>
<tr class="even">
<td><strong>Delete</strong></td>
<td>Click to delete the selected receive location.</td>
</tr>
<tr class="odd">
<td><strong>Properties</strong></td>
<td>Click to open the <strong>Receive Location Properties</strong> window for the selected receive location.</td>
</tr>
<tr class="even">
<td><strong>Name</strong></td>
<td>Displays the name of a receive location.</td>
</tr>
<tr class="odd">
<td><strong>URI</strong></td>
<td>Displays the adapter type and the receive location address.</td>
</tr>
</tbody>
</table>

## Inbound Maps Tab

You can use a map to apply an XSL transformation of an inbound message at the receive port without processing the message through an orchestration. You can add more than one map to a receive port, but each map must have a unique source schema.

The following table lists the UIElements in the **Inbound Maps** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Remove</strong></td>
<td>Click to remove the selected map.</td>
</tr>
<tr class="even">
<td><strong>Source Document</strong></td>
<td>From the drop-down list, select the source schema to use with this port.</td>
</tr>
<tr class="odd">
<td><strong>Map</strong></td>
<td>From the drop-down list, select the map you want to associate with this port.</td>
</tr>
<tr class="even">
<td><strong>Target Document</strong></td>
<td>From the drop-down list, select the destination schema to use with this port.</td>
</tr>
</tbody>
</table>

## Outbound Maps Tab

You can use a map to apply an XSL transformation of a response message sent by the receive port without processing the message through an orchestration. You can add more than one map to a receive port, but each map must have a unique source schema.

The following table lists the UIElements in the **Outbound Maps** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Remove</strong></td>
<td>Click to remove the selected map.</td>
</tr>
<tr class="even">
<td><strong>Source Document</strong></td>
<td>From the drop-down list, select the source schema to use with this port.</td>
</tr>
<tr class="odd">
<td><strong>Map</strong></td>
<td>From the drop-down list, select the map you want to associate with this port.</td>
</tr>
<tr class="even">
<td><strong>Target Document</strong></td>
<td>From the drop-down list, select the destination schema to use with this port.</td>
</tr>
</tbody>
</table>

## Tracking Tab

Message body tracking saves messages after service instances processing is complete. Message property tracking provides a record of promoted properties for each message in the Results list, and enables you to locate a specific message.

> [!NOTE]
> Specific properties that are applicable only to two-way ports are hidden for one-way ports.

The following table lists the UIElements in the **Tracking** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Track Message Bodies - Request message before port processing</strong></td>
<td>Select this check box to enable you to save and track message content before the message is received.</td>
</tr>
<tr class="even">
<td><strong>Track Message Bodies - Request message after port processing</strong></td>
<td>Select this check box to enable you to save and track message content after the message is received.</td>
</tr>
<tr class="odd">
<td><strong>Track Message Properties - Request message before port processing</strong></td>
<td>Select this check box to track the promoted properties of an inbound message.</td>
</tr>
<tr class="even">
<td><strong>Track Message Properties - Request message after port processing</strong></td>
<td>Select this check box if you want to track the promoted properties of an outbound message.</td>
</tr>
<tr class="odd">
<td><strong>Track Message Bodies - Response message before port processing</strong></td>
<td>Select this check box to enable you to save and track message content before the message is sent.</td>
</tr>
<tr class="even">
<td><strong>Track Message Bodies - Response message after port processing</strong></td>
<td>Select this check box to enable you to save and track message content after the message is sent.</td>
</tr>
<tr class="odd">
<td><strong>Track Message Properties - Response message before port processing</strong></td>
<td>Select this check box to track the promoted properties of an outbound message.</td>
</tr>
<tr class="even">
<td><strong>Track Message Properties - Response message after port processing</strong></td>
<td>Select this check box if you want to track the promoted properties of an inbound message.</td>
</tr>
</tbody>
</table>

## See Also

[How to Create a Receive Port](https://msdn.microsoft.com/library/aa559206\(v=bts.80\))
