---
description: "Learn more about: Default Child Delimiter (Node Property of Flat File Schemas)"
title: Default Child Delimiter (Node Property of Flat File Schemas)
TOCTitle: Default Child Delimiter (Node Property of Flat File Schemas)
ms:assetid: cd53f0d9-78ec-41be-9e35-ba2aa1945b25
ms:mtpsurl: https://msdn.microsoft.com/library/Aa548067(v=BTS.80)
ms:contentKeyID: 51531405
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Default Child Delimiter (Node Property of Flat File Schemas)

 

Use the **Default Child Delimiter** property to configure, for the entire schema, the default string used to delimit fields in instance data.

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

## Category

Flat File

## Allowed Values

Either no value, or any string of characters entered in the format indicated by your choice for the [Default Child Delimiter Type](default-child-delimiter-type-node-property-of-flat-file-schemas.md) property.

## Default Value

No value, resulting in no annotation being added to the XSD representation of the schema.

## XSD Persistence

As the value of the **default\_child\_delimiter** attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.

You must configure the **Default Child Delimiter Type** property as **Character** or **Hexadecimal** before you can configure this property.

You can override the global setting established by this property by setting the [Child Delimiter](child-delimiter-node-property-of-flat-file-schemas.md) property for individual **Record** nodes.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

