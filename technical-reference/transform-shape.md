---
title: Transform Shape
TOCTitle: Transform Shape
ms:assetid: 0bf78389-597f-437c-a893-88ec99147f55
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547255(v=BTS.80)
ms:contentKeyID: 51526139
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.shape.transform
---

# Transform Shape

 

You can use the **Transform**shape to move data from one message into another. You specify one or more input messages, one or more output messages, and an XSLT map for the transform. The map assigns message parts from the input messages to message parts in the output messages. You only use transforms in the construction of messages, so your Transform shape always appears inside a Construct Message shape.


> [!NOTE]
> <P>Any source or destination messages in a Transform must be based on a schema.</P>



<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Input Messages</strong> property</td>
<td>Specify which messages will be the source of the data.</td>
</tr>
<tr class="even">
<td><strong>Map Name</strong> property</td>
<td>Specify the name of the XSLT map that will do the transformation.</td>
</tr>
<tr class="odd">
<td><strong>Output Messages</strong> property</td>
<td>Specify which messages will be the destination of the data.</td>
</tr>
<tr class="even">
<td><strong>Report to Analyst</strong> property</td>
<td>Select <strong>True</strong> if you want to make this shape viewable in the Visual Business Analyst Tool.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure the Transform Shape](https://msdn.microsoft.com/library/aa547996\(v=bts.80\))

