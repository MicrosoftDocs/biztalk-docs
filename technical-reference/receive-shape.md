---
title: Receive Shape
TOCTitle: Receive Shape
ms:assetid: 60625f7e-6a95-4822-b302-aae2adae7252
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560440(v=BTS.80)
ms:contentKeyID: 51528412
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.shape.receive
---

# Receive Shape

 

Use the **Receive** shape to receive a message from a port. You can use it to start an orchestration by setting the **Activate** property to **True**, so that a message matching criteria specified in a filter expression will be received and the orchestration instance will execute. You can apply a correlation set to ensure that you correctly receive messages that correspond to a given instance of your orchestration.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Activate</strong> property</td>
<td>Specify whether this is an activation receive by selecting <strong>True</strong> or <strong>False</strong>. If <strong>True</strong>, the <strong>Receive</strong> shape must be the first action in the orchestration. If <strong>False</strong>, your orchestration must be called by another orchestration in order to run. <strong>Note:</strong> Each orchestration must have at least one <strong>Receive</strong> shape with the <strong>Activate</strong> property set to <strong>True</strong>.</td>
</tr>
<tr class="even">
<td><strong>Filter Expression</strong> property</td>
<td>Specify an expression to test properties on the incoming message to decide whether to process it.</td>
</tr>
<tr class="odd">
<td><strong>Initializing Correlation Sets</strong> property</td>
<td>From the drop-down list, select the correlation sets which will be initialized by the values in the sent message.</td>
</tr>
<tr class="even">
<td><strong>Following Correlation Sets</strong> property</td>
<td>From the drop-down list, select already-initialized correlation sets.</td>
</tr>
<tr class="odd">
<td><strong>Message</strong> property</td>
<td>From the drop-down list, select the message to be received.</td>
</tr>
<tr class="even">
<td><strong>Operation</strong> property</td>
<td>From the drop-down list, select the operation in which to receive the message.</td>
</tr>
<tr class="odd">
<td><strong>Report to Analyst</strong> property</td>
<td>Select <strong>True</strong> if you want to make this shape viewable in the Visual Business Analyst Tool.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure the Receive Shape](https://msdn.microsoft.com/library/aa558717\(v=bts.80\))

