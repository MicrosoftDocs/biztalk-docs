---
title: Default Escape Character Type (Node Property of Flat File Schemas)
TOCTitle: Default Escape Character Type (Node Property of Flat File Schemas)
ms:assetid: 8c553aed-9a8f-4713-8add-b1413116213e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561290(v=BTS.80)
ms:contentKeyID: 51529580
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Default Escape Character Type (Node Property of Flat File Schemas)

 

Use the **Default Escape Character Type** property to configure, for the entire schema, how an alternative default escape character will be expressed in the [Default Escape Character](default-escape-character-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation.

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
<td><strong>Character</strong></td>
<td>Indicates that you will provide a default escape character as a character in the <strong>Default Escape Character</strong> property, which will be formatted as a character in the XSD representation of the schema.</td>
</tr>
<tr class="even">
<td><strong>Hexadecimal</strong></td>
<td>Indicates that you will provide the hexadecimal value (&quot;0xNN&quot;) of a default escape character in the <strong>Default Escape Character</strong> property, which will be formatted as a hexadecimal value in the XSD representation of the schema.</td>
</tr>
<tr class="odd">
<td><strong>None</strong></td>
<td>Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that there is no default escape character for the entire schema. You must explicitly specify an appropriate escape character for every <strong>Record</strong> node within the schema.<br />
<br />
Selecting <strong>Default Escape Character</strong> for the value of the <strong>Escape Character</strong> property of any of the <strong>Record</strong> nodes within the schema will result in a compilation error.</td>
</tr>
</tbody>
</table>


## Default Value

**None**, resulting in no annotation being added to the XSD representation of the schema.

## XSD Persistence

As the value of the **escape\_char\_type** (="char" or "hex") attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.

If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Default Escape Character** property in one of these two formats.

This value may be overridden for particular **Record** nodes by using the [Escape Character](escape-character-node-property-of-flat-file-schemas.md) and [Escape Character Type](escape-character-type-node-property-of-flat-file-schemas.md) properties.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

