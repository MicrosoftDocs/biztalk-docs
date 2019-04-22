---
title: Configure Application Dialog Box
TOCTitle: Configure Application Dialog Box
ms:assetid: c4ec8bdf-fad6-4f55-bc2a-63418b322bd6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547889(v=BTS.80)
ms:contentKeyID: 51531039
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.application.configure
---

# Configure Application Dialog Box

 

Use the **Configure Application** dialog box to bind logical ports and role links to physical ports and parties, configure the host under which these execute, and configure send and receive ports, send port groups, and receive port locations. Artifacts in this dialog box must be completely configured or the application will not start.

## Orchestrations Tab

The Orchestrations tab contains a node for each orchestration in the project. Click each orchestration name to view and configure related properties. Applications that are CBR or Messaging applications only do not display an **Orchestrations** tab because no orchestrations are included in the application. The information displayed for each orchestration is identical to the information on the **Bindings** tab in the **Orchestration Properties** window.

### \<Orchestration Name\>

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
<td>From the drop-down list, select a host on which to enlist the application.</td>
</tr>
<tr class="even">
<td><strong>Bindings - Inbound Logical Ports</strong></td>
<td>Displays the name of a logical inbound port. Logical ports are found on the port surfaces in orchestrations.</td>
</tr>
<tr class="odd">
<td><strong>Bindings - Receive Ports</strong></td>
<td>From the drop-down list, select the physical receive port that you want to bind to the corresponding inbound logical port.</td>
</tr>
<tr class="even">
<td><strong>Bindings - Outbound Logical Ports</strong></td>
<td>Displays the name of a logical outbound port. Logical ports are found on the port surfaces in orchestrations.</td>
</tr>
<tr class="odd">
<td><strong>Bindings - Send Ports/Send Port Groups</strong></td>
<td>From the drop-down list, select the send port or send port group that you want to bind to the corresponding outbound logical port.</td>
</tr>
</tbody>
</table>


## Messaging Tab

### Send Ports and Send Port Groups

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
<td><strong>New</strong></td>
<td>Click to create a new send port or send port group. Options for send ports are identical to the options available when you right-click the <strong>Send Ports</strong> node in the Administrative Console tree and point to <strong>New</strong>.</td>
</tr>
<tr class="even">
<td><strong>Properties</strong></td>
<td>Click to display the properties window for the selected send port or send port group. If you select a send port, the <strong>Send Port Properties</strong> window appears, where you can configure the port. If you select a send port group, the <strong>Send Port Groups Properties</strong> window appears, where you can configure the send port group.</td>
</tr>
<tr class="odd">
<td><strong>Name</strong></td>
<td>Displays the name of the physical send ports bound to the orchestration.</td>
</tr>
<tr class="even">
<td><strong>Filter</strong></td>
<td>Displays the filter expression applied to the send port. Filters are set up in the <strong>Send Port Properties</strong> window.</td>
</tr>
<tr class="odd">
<td><strong>URI</strong></td>
<td>Displays the URI for the selected port.</td>
</tr>
</tbody>
</table>


## Receive Ports and Locations

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
<td><strong>New</strong></td>
<td>Click to create a new receive port. Options for new receive ports are identical to the options available when you right-click the <strong>Receive Ports</strong> node in the Administrative Console tree and point to <strong>New</strong>.</td>
</tr>
<tr class="even">
<td><strong>Properties</strong></td>
<td>Click to display the properties window for the selected item. If you have selected a receive port, the <strong>Receive Port Properties</strong> window appears, where you can configure the port. If you have selected a receive port location, the <strong>Receive Locations Properties</strong> window appears, where you can configure the receive location. To select a receive port, click the boldface text to the right of <strong>Receive port</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Name</strong></td>
<td>Displays the name of the receive location associated with a receive port.</td>
</tr>
<tr class="even">
<td><strong>URI</strong></td>
<td>Displays the URI for the selected receive location.</td>
</tr>
</tbody>
</table>


## Role Links Tab

### \<Role Link Name\>

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
<td><strong>Enlist</strong></td>
<td>Click to display the <strong>Enlist Parties</strong> dialog box, where you can select a party to participate in the interchange defined by the role.</td>
</tr>
<tr class="even">
<td><strong>Unenlist</strong></td>
<td>Click to remove the selected party from participating in the interchange.</td>
</tr>
<tr class="odd">
<td><strong>Bind</strong></td>
<td>Click to establish a connection between the role link and the physical ports.</td>
</tr>
<tr class="even">
<td><strong>Party</strong></td>
<td>Displays the name of the party or parties that you have enlisted to this role.</td>
</tr>
</tbody>
</table>


## See Also

[Using the BizTalk Server Administration Console](https://msdn.microsoft.com/library/aa578089\(v=bts.80\))

