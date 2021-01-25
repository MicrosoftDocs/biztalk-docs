---
description: "Learn more about: Call Orchestration Shape"
title: Call Orchestration Shape
TOCTitle: Call Orchestration Shape
ms:assetid: e12af37d-302a-4da5-a2c2-741fc1a4bdf5
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561529(v=BTS.80)
ms:contentKeyID: 51532886
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.shape.call
---

# Call Orchestration Shape

 

The **Call Orchestration** shape invokes another orchestration synchronously; that is, the enclosing orchestration waits for the nested orchestration to finish before continuing.

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
<td>Specify the name of the orchestration that the current orchestration will call.</td>
</tr>
<tr class="even">
<td><strong>Identifier</strong> property</td>
<td>Specify a unique identifier for this shape.</td>
</tr>
<tr class="odd">
<td><strong>Parameters</strong> property</td>
<td>Specify parameters, such as messages, variables, port references, role links, or correlation sets, to be passed to the called orchestration.</td>
</tr>
<tr class="even">
<td><strong>Report to Analyst</strong> property</td>
<td>Select <strong>True</strong> if you want to make this shape viewable in the Visual Business Analyst Tool.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure the Call Orchestration Shape](https://msdn.microsoft.com/library/aa560780\(v=bts.80\))

