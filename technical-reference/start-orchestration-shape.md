---
description: "Learn more about: Start Orchestration Shape"
title: Start Orchestration Shape
TOCTitle: Start Orchestration Shape
ms:assetid: 2c1e9b7f-8797-4225-8d7a-2a427a1ca66e
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559372(v=BTS.80)
ms:contentKeyID: 51527056
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.shape.start
---

# Start Orchestration Shape

 

You use the **Start Orchestration** shape to invoke another orchestration—that is, the flow of control in the invoking orchestration proceeds beyond the invocation, without waiting for the invoked orchestration to finish its work.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Called Orchestration</strong> property</td>
<td>Specify the name of the orchestration that the current orchestration will start.</td>
</tr>
<tr class="even">
<td><strong>Parameters</strong> property</td>
<td>Specify parameters, such as messages, variables, port references, role links, or correlation sets, to be passed to the called orchestration. All parameters are in parameters; you cannot pass out or reference parameters to a started orchestration.</td>
</tr>
<tr class="odd">
<td><strong>Report to Analyst</strong> property</td>
<td>Select <strong>True</strong> if you want to make this shape viewable in the Visual Business Analyst Tool.</td>
</tr>
</tbody>
</table>

