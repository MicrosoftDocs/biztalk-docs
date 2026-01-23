---
description: "Learn more about: Suspend Shape"
title: Suspend Shape
TOCTitle: Suspend Shape
ms:assetid: 76e9ea47-1e32-450a-9532-fa311181567d
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560868(v=BTS.80)
ms:contentKeyID: 51529014
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.shape.suspend
ms.topic: ui-reference
---

# Suspend Shape

 

You can use the **Suspend** shape to make an orchestration instance stop running until an administrator explicitly intervenes, perhaps to reflect an error condition that requires attention beyond the scope of the orchestration. All of the state information for the orchestration instance is saved, and will be reinstated when the administrator resumes the orchestration instance.

When an orchestration instance is suspended, an error is raised. You can specify a message string to accompany the error to help the administrator diagnose the situation.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Error Message</strong> property</td>
<td>Specify an error message to use in diagnosing the situation.</td>
</tr>
<tr class="even">
<td><strong>Report to Analyst</strong> property</td>
<td>Select <strong>True</strong> if you want to make this shape viewable in the Visual Business Analyst Tool.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure the Suspend Shape](https://msdn.microsoft.com/library/aa560486\(v=bts.80\))

