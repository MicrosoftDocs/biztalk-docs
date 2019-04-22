---
title: Decide Shape
TOCTitle: Decide Shape
ms:assetid: 3c3d25ce-8216-4617-a5b8-b481b39937a4
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559689(v=BTS.80)
ms:contentKeyID: 51527424
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.shape.decide
---

# Decide Shape

 

The **Decide** shape represents a decision based on if/else logic. The shape always has a branch for the "if" statement and a branch for the "else" statement; you can add additional branches for "else if" statements as needed. You use the Expression editor to add a rule to each branch except the "else" branch. If the rule evaluates to true, the branch will be taken. Below the rule or "else" clause, a branch of a **Decide**shape can contain additional shapes, just like any other part of the orchestration.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Rule</strong></td>
<td>Right-click the rule to add a Boolean expression to determine whether this rule branch should be taken in your business process.</td>
</tr>
<tr class="even">
<td><strong>Rule</strong> branch</td>
<td>Drag shapes onto this branch to specify any actions to take if the rule in this branch is satisfied.</td>
</tr>
<tr class="odd">
<td><strong>Else</strong> branch</td>
<td>Drag shapes onto this branch to specify any actions to take if none of the rules in other branches are satisfied.</td>
</tr>
<tr class="even">
<td><strong>Report to Analyst</strong> property</td>
<td>Select <strong>True</strong> if you want to make this shape viewable in the Visual Business Analyst Tool.</td>
</tr>
</tbody>
</table>

