---
description: "Learn more about: Default Wrap Character Type (Node Property of Flat File Schemas)"
title: Default Wrap Character Type (Node Property of Flat File Schemas)
TOCTitle: Default Wrap Character Type (Node Property of Flat File Schemas)
ms:assetid: ce329474-ac76-41c7-acb0-a9a6405d7578
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578478(v=BTS.80)
ms:contentKeyID: 51531321
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Default Wrap Character Type (Node Property of Flat File Schemas)

 

Use the **Default Wrap Character Type** property to specify, for the entire schema, how an alternative wrap character will be expressed in the [Default Wrap Character](default-wrap-character-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation.

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
<td>Indicates that you will provide a default wrap character as a character in the <strong>Default Wrap Character</strong> property, which will be formatted as a character in the XSD representation of the schema.</td>
</tr>
<tr class="even">
<td><strong>Hexadecimal</strong></td>
<td>Indicates that you will provide the hexadecimal value (&quot;0xNN&quot;) of a default wrap character in the <strong>Default Wrap Character</strong> property, which will be formatted as a hexadecimal value in the XSD representation of the schema.</td>
</tr>
<tr class="odd">
<td><strong>None</strong></td>
<td>Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that there is no default wrap character for the entire schema. You must explicitly specify an appropriate wrap character for every <strong>Record</strong> node within the schema.<br />
<br />
Selecting <strong>Default Wrap Character</strong> for the value of the <strong>Wrap Character</strong> property of any of the <strong>Record</strong> nodes within the schema will result in a compilation error.</td>
</tr>
</tbody>
</table>


## Default Value

**None**, resulting in no annotation being added to the XSD representation of the schema.

## XSD Persistence

As the value of the **wrap\_char\_type** (="char" or "hex") attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.

If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Default Wrap Character** property in one of these two formats.

Setting the **Default Wrap Character Type** property to **None** removes the annotation from the schema. The parser interprets the absence of the annotation as the default case and uses the **Default Wrap Character**, if set. For more information about the parser processing fields, see the `DocumentSchema.ParseFieldInfo Method`.

You can set the equivalent properties on individual **Field Element** and **Field Attribute** nodes using the [Wrap Character](wrap-character-node-property-of-flat-file-schemas.md) and [Wrap Character Type](wrap-character-type-node-property-of-flat-file-schemas.md) properties. If you set default values for the schema, the default values override values set on individual nodes.

## See Also

[Default Wrap Character (Node Property of Flat File Schemas)](default-wrap-character-node-property-of-flat-file-schemas.md)  
[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)  
[Wrap Character (Node Property of Flat File Schemas)](wrap-character-node-property-of-flat-file-schemas.md)  
[Wrap Character Type (Node Property of Flat File Schemas)](wrap-character-type-node-property-of-flat-file-schemas.md)

