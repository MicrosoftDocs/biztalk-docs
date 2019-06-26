---
title: Role Link Shape
TOCTitle: Role Link Shape
ms:assetid: 6d36cffd-70db-4ed5-a773-1bc33d8c400f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560689(v=BTS.80)
ms:contentKeyID: 51528777
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.shape.role.link
---

# Role Link Shape

 

A **Role Link** shape contains placeholders for an implements role and a uses role. It can include one of either, or one of each.

You can add port types directly to a Role Link shape, using either existing roles or new roles, and existing or new port types.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Identifier</strong> property</td>
<td>Type a unique identifier for this role link.</td>
</tr>
<tr class="even">
<td><strong>Implements Role</strong> property</td>
<td>Click the ellipsis <strong>(…)</strong> button and use the Role Link Wizard to specify the role that this orchestration will play in the role link.</td>
</tr>
<tr class="odd">
<td><strong>Initiating Role</strong> property</td>
<td>From the drop-down list, select the role that initiates this role link.</td>
</tr>
<tr class="even">
<td><strong>Ordered Delivery</strong> property</td>
<td>From the drop-down list, select <strong>True</strong> or <strong>False</strong> to specify whether this role link should use ordered delivery.</td>
</tr>
<tr class="odd">
<td><strong>Report to Analyst</strong> property</td>
<td>Select <strong>True</strong> if you want to make this shape viewable in the Visual Business Analyst Tool.</td>
</tr>
<tr class="even">
<td><strong>Role Link Type</strong> property</td>
<td>Specify a role link type with the Role Link Wizard.</td>
</tr>
<tr class="odd">
<td><strong>Uses Role</strong> property</td>
<td>Click the ellipsis <strong>(…)</strong> button and use the Role Link Wizard to specify the role to which this orchestration will send messages.</td>
</tr>
</tbody>
</table>


## See Also

[How to Use the Role Link Shape](https://msdn.microsoft.com/library/aa561178\(v=bts.80\))

