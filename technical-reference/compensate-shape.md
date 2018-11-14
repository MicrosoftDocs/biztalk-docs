---
title: Compensate Shape
TOCTitle: Compensate Shape
ms:assetid: cc75193c-0193-4891-86e9-f887e5008f4e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa548041(v=BTS.80)
ms:contentKeyID: 51531373
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.shape.compensate
---

# Compensate Shape

 

If you are using nested transactions, you can add a **Compensate** shape in the compensation block or an exception block of a transaction scope, so your orchestration can explicitly perform compensation on a nested transaction. You specify the transaction to compensate, and any compensation code in the nested transaction that will be run. If you want to compensate more than one nested transaction, you add an additional **Compensate** shape for each transaction.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Compensation</strong> property</td>
<td>From the drop-down list, select a transaction on which compensation will be done.</td>
</tr>
<tr class="even">
<td><strong>Report to Analyst</strong> property</td>
<td>Select <strong>True</strong> if you want to make this shape viewable in the Visual Business Analyst Tool.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure the Compensate Shape](https://msdn.microsoft.com/library/aa577630\(v=bts.80\))

