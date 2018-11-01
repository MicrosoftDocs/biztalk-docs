---
title: Child Delimiter Type (Node Property of Flat File Schemas)
TOCTitle: Child Delimiter Type (Node Property of Flat File Schemas)
ms:assetid: 2ac3248a-e2d8-4fd6-b10e-feecb7428dc0
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559342(v=BTS.80)
ms:contentKeyID: 51526941
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Child Delimiter Type (Node Property of Flat File Schemas)

 

Use the **Child Delimiter Type** property to configure, on a per-record basis, how an alternative child delimiter string will be expressed in the [Child Delimiter](child-delimiter-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation, or whether the default child delimiter string will be used.

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
<td><strong>Character</strong></td>
<td>Specifies that you will provide a child delimiter string as characters in the <strong>Child Delimiter</strong> property, which will be formatted as characters in the XSD representation of the schema.</td>
</tr>
<tr class="even">
<td><strong>Hexadecimal</strong></td>
<td>Specifies that you will provide the hexadecimal value (&quot;0xNNNN&quot;) of a child delimiter string in the <strong>Child Delimiter</strong> property, which will be formatted as a hexadecimal value in the XSD representation of the schema.</td>
</tr>
<tr class="odd">
<td><strong>Default Child Delimiter</strong></td>
<td>Specifies that the delimiter specified using the <a href="default-child-delimiter-node-property-of-flat-file-schemas.md">Default Child Delimiter</a> property will be used.</td>
</tr>
<tr class="even">
<td><strong>None</strong></td>
<td>Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that there is no child delimiter for this <strong>Record</strong> node. If more than one child node is specified in the schema, this setting will result in a warning during compilation.</td>
</tr>
</tbody>
</table>


## Default Value

**None**, resulting in no annotation being added to the XSD representation of the schema.

## XSD Persistence

As the value of the **child\_delimiter\_type** (="char", "hex", or "default") attribute of the **element/annotation/appinfo/recordInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you have:

  - Selected a **Record** node (including a root **Record** node) in BizTalk Editor

  - Set the **Structure** property of the selected **Record** node to **Delimited**

  - Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node

If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Child Delimiter** property in one of these two formats.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

