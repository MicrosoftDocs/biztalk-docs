---
title: Throw Exception Shape
TOCTitle: Throw Exception Shape
ms:assetid: b51b38c6-162e-4e38-9fc6-73ba639814ca
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578219(v=BTS.80)
ms:contentKeyID: 51530648
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.shape.exception.throw
---

# Throw Exception Shape

 

You can explicitly throw exceptions in an orchestration with the **Throw Exception** shape. The run-time engine searches for the nearest exception handler that can handle the exception type. It first searches the current orchestration for an enclosing scope, and then considers in order the associated exception handlers of the scope. If the engine does not find an appropriate handler, it searches any orchestration that called the current orchestration for a scope that encloses the point of the call to the current orchestration.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Exception Object</strong> property</td>
<td>Specify the type of the exception being thrown.</td>
</tr>
<tr class="even">
<td><strong>Report to Analyst</strong> property</td>
<td>Select <strong>True</strong> if you want to make this shape viewable in the Visual Business Analyst Tool.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure the Throw Exception Shape](https://msdn.microsoft.com/library/aa578573\(v=bts.80\))

