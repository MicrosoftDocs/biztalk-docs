---
description: "Learn more about: Wrap Character Type (Node Property of Flat File Schemas)"
title: Wrap Character Type (Node Property of Flat File Schemas)
TOCTitle: Wrap Character Type (Node Property of Flat File Schemas)
ms:assetid: 650d45fd-3afd-44f0-a828-d212168b6d4b
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560522(v=BTS.80)
ms:contentKeyID: 51528535
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Wrap Character Type (Node Property of Flat File Schemas)

 

Use the **Wrap Character Type** property to configure, on a per-field basis, how an alternative wrap character will be expressed in the [Wrap Character](wrap-character-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation, or whether the default wrap character will be used.

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
<td>Indicates that you will provide a wrap character as a character in the <strong>Wrap Character</strong> property, which will be formatted as a character in the XSD representation of the schema.</td>
</tr>
<tr class="even">
<td><strong>Hexadecimal</strong></td>
<td>Indicates that you will provide the hexadecimal value (&quot;0xNN&quot;) of a wrap character in the <strong>Wrap Character</strong> property, which will be formatted as a hexadecimal value in the XSD representation of the schema.</td>
</tr>
<tr class="odd">
<td><strong>Default Wrap Character</strong></td>
<td>Use this value if you want to use the default wrap character for the entire schema, as established by the <a href="default-wrap-character-node-property-of-flat-file-schemas.md">Default Wrap Character</a> property of the <strong>Schema</strong> node.</td>
</tr>
<tr class="even">
<td><strong>None</strong></td>
<td>Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that there is no wrap character specified for the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.<br />
<br />
The <a href="wrap-character-node-property-of-flat-file-schemas.md">Wrap Character</a> property should not be set to any value when this property is set to <strong>None</strong>.</td>
</tr>
</tbody>
</table>


## Default Value

**None**, resulting in no corresponding annotation in the XSD representation of the schema, and specifying that there is no wrap character specified for the selected **Field Element** or **Field Attribute** node.

## XSD Persistence

As the value of the **wrap\_char\_type** (="char", "hex", or "default") attribute of:

  - For **Field Element** nodes, the **element/annotation/appinfo/fieldInfo** annotation element.

  - For **Field Attribute** nodes, the **attribute/annotation/appinfo/fieldInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have:

  - Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node

  - Set the **Structure** property of the containing **Record** node to **Delimited**

If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Wrap Character** property in one of these two formats.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

