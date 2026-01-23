---
description: "Learn more about: Escape Character Type (Node Property of Flat File Schemas)"
title: Escape Character Type (Node Property of Flat File Schemas)
TOCTitle: Escape Character Type (Node Property of Flat File Schemas)
ms:assetid: d2aac497-80e9-49f8-a0c7-64e23aa323a4
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578565(v=BTS.80)
ms:contentKeyID: 51531444
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Escape Character Type (Node Property of Flat File Schemas)

 

Use the **Escape Character Type** property to configure, on a per-record basis, how an alternative escape character will be expressed in the [Escape Character](escape-character-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation, or whether the default escape character will be used.

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
<td>Indicates that you will provide an escape character as a character in the <strong>Escape Character</strong> property, which will be formatted as a character in the XSD representation of the schema.</td>
</tr>
<tr class="even">
<td><strong>Hexadecimal</strong></td>
<td>Indicates that you will provide the hexadecimal value (&quot;0xNN&quot;) of an escape character in the <strong>Escape Character</strong> property, which will be formatted as a hexadecimal value in the XSD representation of the schema.</td>
</tr>
<tr class="odd">
<td><strong>Default Escape Character</strong></td>
<td>Use this value if you want to use the default escape character for the entire schema, as established by the <a href="default-escape-character-node-property-of-flat-file-schemas.md">Default Escape Character</a> property of the <strong>Schema</strong> node.</td>
</tr>
<tr class="even">
<td><strong>None</strong></td>
<td>Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that there is no escape character defined for this <strong>Record</strong> node.<br />
<br />
The <a href="escape-character-node-property-of-flat-file-schemas.md">Escape Character</a> property should not be set to any value when this property is set to <strong>None</strong>.</td>
</tr>
</tbody>
</table>


## Default Value

**None**, resulting in no annotation being added to the XSD representation of the schema.

## XSD Persistence

As the value of the **escape\_char\_type** (="char", "hex", or "default") attribute of the **element/annotation/appinfo/recordInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node.

If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Escape Character** property in one of these two formats.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

