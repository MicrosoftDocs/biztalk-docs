---
title: Count Positions In Bytes (Node Property of Flat File Schemas)
TOCTitle: Count Positions In Bytes (Node Property of Flat File Schemas)
ms:assetid: 56eccdab-d4fb-4f8b-b39d-b269929b30c2
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560258(v=BTS.80)
ms:contentKeyID: 51528164
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Count Positions In Bytes (Node Property of Flat File Schemas)

 

Use the **Count Positions In Bytes** property to configure whether the positions will be counted in bytes rather than characters.

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

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
<td><strong>Yes</strong></td>
<td>Sets the <strong>count_positions_by_bytes</strong> attribute to &quot;true&quot;, specifying that position counting should be done by bytes.</td>
</tr>
<tr class="even">
<td><strong>No</strong></td>
<td>Sets the <strong>count_positions_by_bytes</strong> attribute to &quot;false&quot;, specifying that position counting should be done by characters.</td>
</tr>
</tbody>
</table>


## Default Value

**No**

## XSD Persistence

As the value of the **count\_positions\_by\_bytes** attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

