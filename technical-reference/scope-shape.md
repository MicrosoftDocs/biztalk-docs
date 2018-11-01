---
title: Scope Shape
TOCTitle: Scope Shape
ms:assetid: ff3a3a49-526b-4e54-8071-ba82c801a281
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa562165(v=BTS.80)
ms:contentKeyID: 51533825
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.shape.scope
---

# Scope Shape

 

The **Scope** shape provides a contextual framework for its contents. The first block of a Scope shape is the context block, or body, in which the basic actions of the scope take place; it is analogous to the try block in a try/catch statement. Following the body, the Scope shape may also include one or more exception-handler blocks and a compensation block.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Batch</strong> property</td>
<td>This property is not used in BizTalk Server and it will be deprecated in the future release.</td>
</tr>
<tr class="even">
<td><strong>Compensation</strong> property</td>
<td>From the drop-down list, select <strong>Default</strong> or <strong>Custom</strong> to specify what type of compensation to perform on the scope.</td>
</tr>
<tr class="odd">
<td><strong>Isolation Level</strong> property</td>
<td>From the drop-down list, select the degree to which data is accessible among concurrent transactions:<br />
<br />
- Read Committed—Prevent the selected transaction from accessing data modifications in concurrent transactions until they are committed. This option is the Microsoft SQL Server default setting.<br />
- Repeatable Read—Require read locks until the selected transaction is complete.<br />
- Serializable—Prevent concurrent transactions from making data modifications until the selected transaction is complete. This option is the most restrictive isolation level.</td>
</tr>
<tr class="even">
<td><strong>Report to Analyst</strong> property</td>
<td>Select <strong>True</strong> if you want to make this shape viewable in the Visual Business Analyst Tool.</td>
</tr>
<tr class="odd">
<td><strong>Retry</strong> property</td>
<td>From the drop-down list, select <strong>True</strong> or <strong>False</strong> to specify whether to retry the transaction if it fails.</td>
</tr>
<tr class="even">
<td><strong>Synchronized</strong> property</td>
<td>From the drop-down list, select <strong>True</strong> or <strong>False</strong> to specify whether the scope is synchronized, which guarantees that shared data accessed within the scope will not be written to by a parallel action until the current scope has completed.</td>
</tr>
<tr class="odd">
<td><strong>Timeout</strong> property</td>
<td>Enter an expression to specify the time in seconds until the transaction fails due to inactivity. If you do not want to use a time-out, set the value of this property to 0.</td>
</tr>
<tr class="even">
<td><strong>Transaction Identifier</strong> property</td>
<td>If this scope is transactional, specify an identifier for the transaction.</td>
</tr>
<tr class="odd">
<td><strong>Transaction Type</strong> property</td>
<td>Specify whether this scope is an atomic transaction, a long-running transaction, or not a transaction. Different properties are available to you depending on the type.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure the Scope Shape](https://msdn.microsoft.com/en-us/library/aa559692\(v=bts.80\))

