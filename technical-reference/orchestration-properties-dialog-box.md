---
description: "Learn more about: Orchestration Properties Dialog Box"
title: Orchestration Properties Dialog Box
TOCTitle: Orchestration Properties Dialog Box
ms:assetid: eb5af3a9-a9bd-4c11-a961-6a203f2a9d24
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561744(v=BTS.80)
ms:contentKeyID: 51533172
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.orchestration.properties
---

# Orchestration Properties Dialog Box

 

Use the **Orchestration Properties** window to view and configure information about the orchestration you have selected in the details pane.

## General Tab

The name and assembly information on the **General** tab are created when you create the orchestration in Microsoft Visual Studio. You can add information to the **Description** box at any time.

## UIElement List

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
<td>Displays the orchestration name and the .NET assembly that contains it.</td>
</tr>
<tr class="even">
<td><strong>Assembly</strong></td>
<td>Displays the fully qualified name (name, version, culture, public key token) of the assembly that contains the orchestration.</td>
</tr>
<tr class="odd">
<td><strong>Description</strong></td>
<td>Type any text that will help you distinguish this orchestration from others. The maximum number of characters allowed is 256.</td>
</tr>
</tbody>
</table>


## Bindings Tab

## UIElement List

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Host</strong></td>
<td>From the drop-down list, select the Host on which to enlist an orchestration.</td>
</tr>
<tr class="even">
<td><strong>Bindings</strong></td>
<td>From the drop-down lists under Receive Ports and Send Ports/Send Port Groups, select Send and Receive ports to bind to respective logical ports.</td>
</tr>
</tbody>
</table>


## Tracking Tab

## UIElement List

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Track Events - Orchestration start and end</strong></td>
<td>Select this check box to track the orchestration instance before and after processing of the entire business process. Orchestration tracking enables you to see the instances in the message event and service instance tracking queries from the Group Hub page.</td>
</tr>
<tr class="even">
<td><strong>Track Events - Message send and receive</strong></td>
<td>Select this check box to track message send and receive events. This check box is available only if you select the <strong>Orchestration start and end</strong> check box.</td>
</tr>
<tr class="odd">
<td><strong>Track Events - Shape start and end</strong></td>
<td>Select this check box when you need to debug orchestration instances in the Orchestration Debugger. When this check box is selected, the event list in the Orchestration Debugger is populated. This check box is available only if you select the <strong>Orchestration start and end</strong> check box.</td>
</tr>
<tr class="even">
<td><strong>Track Message Bodies - Messages before orchestration processing</strong></td>
<td>Select this check box to save and track the actual message content prior to processing by the orchestration instance. This check box is available only if you select the <strong>Message send and receive</strong> check box.</td>
</tr>
<tr class="odd">
<td><strong>Track Message Bodies - Messages after orchestration processing</strong></td>
<td>Select this check box to save and track the actual message content after processing by the orchestration instance. This check box is available only if you select the <strong>Message send and receive</strong> check box.</td>
</tr>
<tr class="even">
<td><strong>Track Message Properties - Incoming messages</strong></td>
<td>Select this check box to track the promoted properties of an inbound message.</td>
</tr>
<tr class="odd">
<td><strong>Track Message Properties - Outgoing messages</strong></td>
<td>Select this check box to track the promoted properties of an outbound message.</td>
</tr>
</tbody>
</table>


## See Also

[Creating Orchestrations](https://msdn.microsoft.com/library/aa577489\(v=bts.80\))  
[About Orchestrations](https://msdn.microsoft.com/library/aa578451\(v=bts.80\))  
[How to Enlist an Orchestration](https://msdn.microsoft.com/library/aa578153\(v=bts.80\))

