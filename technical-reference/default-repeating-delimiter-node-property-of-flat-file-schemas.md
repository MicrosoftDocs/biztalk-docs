---
title: Default Repeating Delimiter (Node Property of Flat File Schemas)
TOCTitle: Default Repeating Delimiter (Node Property of Flat File Schemas)
ms:assetid: e58aa100-eebc-449f-8d8f-58803b154205
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561625(v=BTS.80)
ms:contentKeyID: 51533002
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Default Repeating Delimiter (Node Property of Flat File Schemas)

 

Use the **Default Repeating Delimiter** property to configure, for the entire schema, the default string used to delimit repeating fields in instance data.

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

## Category

Flat File

## Allowed Values

Either:

  - No value, resulting in no annotation being added to the XSD representation of the schema. This value is only allowed when the [Default Repeating Delimiter Type](default-repeating-delimiter-type-node-property-of-flat-file-schemas.md) property is set to **None**.

  - Any string of characters entered in the format indicated by your choice for the **Default Repeating Delimiter Type** property.

## Default Value

No value, resulting in no annotation being added to the XSD representation of the schema.

## XSD Persistence

As the value of the **default\_repeating\_delimiter** attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.

You must configure the **Default Repeating Delimiter Type** property as **Character** or **Hexadecimal** before you can configure this property.

You can override the global setting established by this property by setting the [Repeating Delimiter](repeating-delimiter-node-property-of-flat-file-schemas.md) property for individual **Record** nodes.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

