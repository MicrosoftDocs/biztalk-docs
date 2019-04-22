---
title: Port Configuration Wizard
TOCTitle: Port Configuration Wizard
ms:assetid: 73a30b25-5983-4254-a561-bca03783a9ec
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560821(v=BTS.80)
ms:contentKeyID: 51528937
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.port.config.wizard
---

# Port Configuration Wizard

 

The Port Configuration Wizard enables you to configure all of the details associated with a port, including port type, pattern of communication, access restrictions, communication direction, and binding information.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Communication pattern</strong></td>
<td>Select <strong>One-Way</strong> to specify that messages will always move in a single direction through this port, or select <strong>Request-Response</strong> if the port will be used for a request-response combination.</td>
</tr>
<tr class="even">
<td><strong>Access restrictions</strong></td>
<td>Select the scope within which this port is accessible.</td>
</tr>
<tr class="odd">
<td><strong>Port direction of communication</strong></td>
<td>From the drop-down list, specify that this port will send messages, receive them, or, in the case of a request-response combination, first send and then receive, or first receive and then send.</td>
</tr>
<tr class="even">
<td><strong>Port binding: Specify later</strong></td>
<td>Defer configuration of this port; in this case, it will be configured at deployment time.</td>
</tr>
<tr class="odd">
<td><strong>Port binding: Specify now</strong></td>
<td>Type a URI to which the port will be bound. From the <strong>Transport</strong> drop-down list, select a transport type. From the available pipeline drop-down list, select a pipeline for the port.</td>
</tr>
<tr class="even">
<td><strong>Port binding: Direct</strong></td>
<td>Use the radio buttons to specify that this port will communicate directly with another port, will be self-correlating, or will use filter expressions to subscribe to incoming messages.</td>
</tr>
</tbody>
</table>


## See Also

[How to Run the Port Configuration Wizard](https://msdn.microsoft.com/library/aa561061\(v=bts.80\))

