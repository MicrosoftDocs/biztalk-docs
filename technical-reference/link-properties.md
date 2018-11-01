---
title: Link Properties
TOCTitle: Link Properties
ms:assetid: a3a16232-507c-4536-9584-de483a9bf220
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577850(v=BTS.80)
ms:contentKeyID: 51530234
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Link Properties

 

The grid pages of BizTalk Mapper graphically depict the structure of the data transformation defined by the map. A link appears as a single line that makes one of the following connections:

  - A node in the source schema to a node in the destination schema

  - A node in the source schema to a functoid

  - A functoid to a node in the destination schema

  - One functoid to another functoid, which is known as cascading functoids

Links depict a transformation, or a step in the transformation, of data from a source instance message into a destination instance message. The left end of the link depicts the source of the transformation (step) and the right end of the link depicts the destination, or target, of the transformation (step).


> [!NOTE]
> <P>When working with links and link properties, the words "destination" and "target" are used interchangeably.</P>



The following table describes the properties of links.

<table>
<thead>
<tr class="header">
<th>Property name</th>
<th>Category</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="label-link-property.md">Label</a></td>
<td>General</td>
<td>Provides a descriptive name for the link that is useful for input links to the <strong>Table Looping</strong> functoid.</td>
</tr>
<tr class="even">
<td><a href="link-source-link-property.md">Link Source</a></td>
<td>General</td>
<td>Allows the source (left end) of the link to be examined in a non-graphical manner.</td>
</tr>
<tr class="odd">
<td><a href="link-target-link-property.md">Link Target</a></td>
<td>General</td>
<td>Allows the destination (right end) of the link to be examined in a non-graphical manner.</td>
</tr>
<tr class="even">
<td><a href="source-links-link-property.md">Source Links</a></td>
<td>Compiler</td>
<td>Specifies the source of the data that will be copied to the destination of the link.</td>
</tr>
<tr class="odd">
<td><a href="target-links-link-property.md">Target Links</a></td>
<td>Compiler</td>
<td>Specifies the type of node hierarchy matching associated with the link and controls how auto-linking is performed.</td>
</tr>
</tbody>
</table>

