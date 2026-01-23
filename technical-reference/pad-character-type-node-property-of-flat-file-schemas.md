---
description: "Learn more about: Pad Character Type (Node Property of Flat File Schemas)"
title: Pad Character Type (Node Property of Flat File Schemas)
TOCTitle: Pad Character Type (Node Property of Flat File Schemas)
ms:assetid: 4a1df473-ed54-4b49-8171-a6570a6d5f88
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559973(v=BTS.80)
ms:contentKeyID: 51527825
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
---

# Pad Character Type (Node Property of Flat File Schemas)

 

Use the **Pad Character Type** property to configure, on a per-field basis, how an alternative pad character will be expressed in the [Pad Character](pad-character-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation, or whether the default pad character will be used.

## Applies to Nodes of Type

[Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

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
<td>Indicates that you will provide a pad character as a character in the <strong>Pad Character</strong> property, which will be formatted as a character in the XSD representation of the schema.</td>
</tr>
<tr class="even">
<td><strong>Hexadecimal</strong></td>
<td>Indicates that you will provide the hexadecimal value (&quot;0xNN&quot;) of a pad character in the <strong>Decimal Character</strong> property, which will be formatted as a hexadecimal value in the XSD representation of the schema.</td>
</tr>
<tr class="odd">
<td><strong>(Default)/ Default Pad Character Type</strong></td>
<td>Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that the default pad character, space (&quot; &quot;), be used.</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, resulting in no annotation being added to the XSD representation of the schema, and specifying that the default pad character, space (" "), be used.

## XSD Persistence

As the value of the **pad\_char\_type** (="char" or "hex") attribute of:

  - For **Field Element** nodes, the **element/annotation/appinfo/fieldInfo** annotation element.

  - For **Field Attribute** nodes, the **attribute/annotation/appinfo/fieldInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node.

If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Pad Character** property in one of these two formats.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

