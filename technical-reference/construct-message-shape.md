---
title: Construct Message Shape
TOCTitle: Construct Message Shape
ms:assetid: bd57a22d-d6ee-41da-a0f8-f28c61af64f3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578383(v=BTS.80)
ms:contentKeyID: 51530876
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.shape.message.construct
---

# Construct Message Shape

 

Use the **Construct Message** shape to construct a new instance of a multipart message type. It must contain either a **Message Assignment** shape or a **Transform** shape, and can contain any number of either, but no other shapes. You specify the message variable that you want to construct, and make assignments to the message or its parts. All assignments to any given message must take place within the same **Construct Message** shape. If you want to modify a property on a message that has already been constructed—such as a message that has been received—you must construct a new message instance by assigning the first to the second and then modifying the property on the new message instance; both the construction and modification occur within the same **Construct Message** shape.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Messages Constructed</strong> property</td>
<td>From the drop-down list, select the names of any messages that will be constructed in this shape.</td>
</tr>
<tr class="even">
<td><strong>Report to Analyst</strong> property</td>
<td>Select <strong>True</strong> if you want to make this shape viewable in the Visual Business Analyst Tool.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure the Construct Message Shape](https://msdn.microsoft.com/library/aa561304\(v=bts.80\))

