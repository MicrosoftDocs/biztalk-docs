---
description: "Learn more about: Structure (Node Property of Flat File Schemas)"
title: Structure (Node Property of Flat File Schemas)
TOCTitle: Structure (Node Property of Flat File Schemas)
ms:assetid: db8bc83f-cb46-47b1-95ac-cebb57ae776c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561411(v=BTS.80)
ms:contentKeyID: 51531708
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Structure (Node Property of Flat File Schemas)

 

Use the **Structure** property to configure whether this non-XML record is positional or delimited.

## Applies to Nodes of Type

[Record](record-node-properties.md)

## Category

Flat File

## Allowed Values

<table>
<thead>
<tr class="header">
<th>Drop-down list choice</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Delimited</strong></td>
<td>Indicates that instance data corresponding to the currently selected record is delimited.</td>
</tr>
<tr class="even">
<td><strong>Positional</strong></td>
<td>Indicates that instance data corresponding to the currently selected record is positional.</td>
</tr>
</tbody>
</table>


## Default Value

**Delimited**, indicating that instance data corresponding to the currently selected record is delimited.

## XSD Persistence

As the value of the **structure** (="delimited" or "positional") attribute of the **element/annotation/appinfo/recordInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node.

The setting of this property plays a major role in determining which other properties are available (visible).

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

