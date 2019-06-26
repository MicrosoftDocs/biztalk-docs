---
title: Repeating Delimiter Type (Node Property of Flat File Schemas)
TOCTitle: Repeating Delimiter Type (Node Property of Flat File Schemas)
ms:assetid: 99852a46-ef7a-48a5-b4ff-d76a24e34c50
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577494(v=BTS.80)
ms:contentKeyID: 51529878
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Repeating Delimiter Type (Node Property of Flat File Schemas)

 

Use the **Repeating Delimiter Type** property to configure, on a per-record basis, how an alternative repeating delimiter string will be expressed in the [Repeating Delimiter](repeating-delimiter-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation, or whether the default repeating delimiter string will be used.

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
<td>Indicates that you will provide a repeating delimiter string as characters in the <strong>Repeating Delimiter</strong> property, which will be formatted as characters in the XSD representation of the schema.</td>
</tr>
<tr class="even">
<td><strong>Hexadecimal</strong></td>
<td>Indicates that you will provide the hexadecimal value (&quot;0xNNNN&quot;) of a repeating delimiter string in the <strong>Repeating Delimiter</strong> property, which will be formatted as a hexadecimal value in the XSD representation of the schema.</td>
</tr>
<tr class="odd">
<td><strong>Default Repeating Delimiter</strong></td>
<td>Use this value if you want to use the default repeating delimiter string for the entire schema, as established by the <a href="default-repeating-delimiter-node-property-of-flat-file-schemas.md">Default Repeating Delimiter</a> property of the <strong>Schema</strong> node.</td>
</tr>
<tr class="even">
<td><strong>None</strong></td>
<td>Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that there is no repeating delimiter specified for the selected <strong>Record</strong> node.<br />
<br />
The <a href="repeating-delimiter-node-property-of-flat-file-schemas.md">Repeating Delimiter</a> property should not be set to any value when this property is set to <strong>None</strong>.</td>
</tr>
</tbody>
</table>


## Default Value

**None**, resulting in no annotation being added to the XSD representation of the schema, and specifying that there is no repeating delimiter specified for the selected **Record** node.

## XSD Persistence

As the value of the **repeating\_delimiter\_type** (="char", "hex", or "default") attribute of the **element/annotation/appInfo/recordInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor and you have:

  - Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node

  - Set the **Structure** property of the selected **Record** node to **Delimited**

If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Repeating Delimiter** property in one of these two formats.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

