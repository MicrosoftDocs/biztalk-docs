---
description: "Learn more about: Default Repeating Delimiter Type (Node Property of Flat File Schemas)"
title: Default Repeating Delimiter Type (Node Property of Flat File Schemas)
TOCTitle: Default Repeating Delimiter Type (Node Property of Flat File Schemas)
ms:assetid: 187a13dc-e17b-4171-b2a4-8df13da5223e
ms:mtpsurl: https://msdn.microsoft.com/library/Aa558797(v=BTS.80)
ms:contentKeyID: 51526475
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Default Repeating Delimiter Type (Node Property of Flat File Schemas)

 

Use the **Default Repeating Delimiter Type** property to configure, for the entire schema, how a default alternative repeating delimiter string will be expressed in the [Default Repeating Delimiter](default-repeating-delimiter-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation.

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
<td>Indicates that you will provide a default repeating delimiter string as characters in the <strong>Default Repeating Delimiter</strong> property, which will be formatted as characters in the XSD representation of the schema.</td>
</tr>
<tr class="even">
<td><strong>Hexadecimal</strong></td>
<td>Indicates that you will provide the hexadecimal value (&quot;0xNNNN&quot;) of a default repeating delimiter string in the <strong>Default Repeating Delimiter</strong> property, which will be formatted as a hexadecimal value in the XSD representation of the schema.</td>
</tr>
<tr class="odd">
<td><strong>None</strong></td>
<td>Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that there is no default repeating delimiter for the entire schema. You must explicitly specify an appropriate repeating delimiter for every <strong>Record</strong> node within the schema.<br />
<br />
Selecting <strong>Default Repeating Delimiter</strong> for the value of the <strong>Repeating Delimiter</strong> property of any of the <strong>Record</strong> nodes within the schema will result in a compilation error.</td>
</tr>
</tbody>
</table>


## Default Value

**None**, resulting in no annotation being added to the XSD representation of the schema.

## XSD Persistence

As the value of the **repeating\_delimiter\_type** (="char" or "hex") attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.

If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Default Repeating Delimiter** property in one of these two formats.

This value may be overridden for particular **Record** nodes by using the [Repeating Delimiter](repeating-delimiter-node-property-of-flat-file-schemas.md) and [Repeating Delimiter Type](repeating-delimiter-type-node-property-of-flat-file-schemas.md) properties.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)  
[Repeating Delimiter (Node Property of Flat File Schemas)](repeating-delimiter-node-property-of-flat-file-schemas.md)

