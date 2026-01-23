---
description: "Learn more about: Default Child Delimiter Type (Node Property of Flat File Schemas)"
title: Default Child Delimiter Type (Node Property of Flat File Schemas)
TOCTitle: Default Child Delimiter Type (Node Property of Flat File Schemas)
ms:assetid: 9dac5ce2-c9af-4344-86b9-83ef40db3a6e
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577588(v=BTS.80)
ms:contentKeyID: 51529979
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Default Child Delimiter Type (Node Property of Flat File Schemas)

 

Use the **Default Child Delimiter Type** property to configure, for the entire schema, how an alternative default child delimiter string will be expressed in the [Default Child Delimiter](default-child-delimiter-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation.

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
<td>Indicates that you will provide a default child delimiter string as characters in the <strong>Default Child Delimiter</strong> property, which will be formatted as characters in the XSD representation of the schema.</td>
</tr>
<tr class="even">
<td><strong>Hexadecimal</strong></td>
<td>Indicates that you will provide the hexadecimal value (&quot;0xNNNN&quot;) of a default child delimiter string in the <strong>Default Child Delimiter</strong> property, which will be formatted as a hexadecimal value in the XSD representation of the schema.</td>
</tr>
<tr class="odd">
<td><strong>None</strong></td>
<td>Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that there is no default child delimiter for the entire schema. You must explicitly specify an appropriate child delimiter for every <strong>Record</strong> node within the schema.<br />
<br />
Selecting <strong>Default Child Delimiter</strong> for the value of the <strong>Child Delimiter Type</strong> property of any of the <strong>Record</strong> nodes within the schema will result in a compilation error.</td>
</tr>
</tbody>
</table>


## Default Value

**None**, resulting in no annotation being added to the XSD representation of the schema.

## XSD Persistence

As the value of the **child\_delimiter\_type** (="char" or "hex") attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.

If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Default Child Delimiter** property in one of these two formats.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

