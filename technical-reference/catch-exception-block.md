---
description: "Learn more about: Catch Exception Block"
title: Catch Exception Block
TOCTitle: Catch Exception Block
ms:assetid: c3545960-9ea0-409e-8a36-c5c6c49dd435
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547861(v=BTS.80)
ms:contentKeyID: 51531002
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.exception.catch.block
---

# Catch Exception Block

 

The **Catch Exception** block represents an exception handler, and is attached to the end of a **Scope** shape. You can attach as many **Catch Exception** blocks as you need. If an exception is thrown that matches the type specified, the exception handler will be called. If some other exception is thrown, it will be handled by the default exception handler.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Exception Object Name</strong> property</td>
<td>Type a name for the exception.</td>
</tr>
<tr class="even">
<td><strong>Exception Object Type</strong> property</td>
<td>From the drop-down list, select an exception type consisting of either a fault message or an object derived from the class <strong>System.Exception</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Report to Analyst</strong> property</td>
<td>Select <strong>True</strong> if you want to make this shape viewable in the Visual Business Analyst Tool.</td>
</tr>
</tbody>
</table>


## See Also

[How to Add a Catch Exception Block](https://msdn.microsoft.com/library/aa560499\(v=bts.80\))

