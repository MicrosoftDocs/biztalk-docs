---
description: "Learn more about: Listen Branch"
title: Listen Branch
TOCTitle: Listen Branch
ms:assetid: 76f40f18-8df3-4992-9030-8084ae700683
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560869(v=BTS.80)
ms:contentKeyID: 51529013
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.branch.listen
---

# Listen Branch

 

The first branch in a **Listen** shape for which a condition is met (a delay is reached or a message is received) will run, and none of the other branches will run. The first shape within a Listen branch must be either a Delay shape or a Receive shape. You can place any other shape below the initial Receive or Delay shape. You can use an activation receive in a Listen branch, but if one branch contains an activation receive, then all branches must contain activation receives, and no time-out can be used. The activation receive must be the first action in each branch.

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
<td>If the branch contains a Receive shape, select <strong>True</strong> or <strong>False</strong> to specify whether it is an activation receive.</td>
</tr>
<tr class="even">
<td><strong>Branch Type</strong> property</td>
<td>From the drop-down list, select either Receive or Delay to specify the type of the branch. Different properties will be available to you depending on the branch type.</td>
</tr>
<tr class="odd">
<td><strong>Delay</strong> property</td>
<td>Specify a time-out using <strong>System.DateTime</strong> or <strong>System.TimeSpan</strong> in order to create a corresponding delay in your orchestration. For example, if you specify <strong>System.DateTime.UtcNow.AddSeconds (60)</strong>, your orchestration will be idle for sixty seconds before proceeding.</td>
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
<td>If the branch contains a Receive shape, select the message to be received from the drop-down list.</td>
</tr>
<tr class="even">
<td><strong>Operation</strong> property</td>
<td>If the branch contains a Receive shape, select the operation represented by the receive from the drop-down list.</td>
</tr>
<tr class="odd">
<td><strong>Report to Analyst</strong> property</td>
<td>Select <strong>True</strong> if you want to make this shape viewable in the Visual Business Analyst Tool.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure the Listen Shape](https://msdn.microsoft.com/library/aa559905\(v=bts.80\))

