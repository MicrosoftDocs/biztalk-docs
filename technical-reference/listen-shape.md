---
description: "Learn more about: Listen Shape"
title: Listen Shape
TOCTitle: Listen Shape
ms:assetid: 983a0ed0-b964-4736-afb7-5ba4aff4b75d
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577476(v=BTS.80)
ms:contentKeyID: 51529908
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.shape.listen
---

# Listen Shape

 

You use the **Listen** shape to make your orchestration wait for any one of several possible events before proceeding. The first branch for which a condition is met (a delay is reached or a message is received) is followed, and none of the other branches will run. You can add as many branches as you want. The first shape within a **Listen** branch must be either a **Delay** shape or a **Receive** shape. You can place any other shape below the initial **Receive** or **Delay** shape. You can use an activation receive in a **Listen** shape, but if one branch contains an activation receive, then all branches must contain activation receives, and no time-out can be used. The activation receive must be the first action in each branch.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Report to Analyst</strong> property</td>
<td>Select <strong>True</strong> if you want to make this shape viewable in the Visual Business Analyst Tool.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure the Listen Shape](https://msdn.microsoft.com/library/aa559905\(v=bts.80\))

