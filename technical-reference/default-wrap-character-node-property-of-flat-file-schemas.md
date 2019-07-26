---
title: Default Wrap Character (Node Property of Flat File Schemas)
TOCTitle: Default Wrap Character (Node Property of Flat File Schemas)
ms:assetid: 27d1b870-fda7-43cc-941f-5122f5a4e5f4
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559288(v=BTS.80)
ms:contentKeyID: 51526867
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Default Wrap Character (Node Property of Flat File Schemas)

 

Use the **Default Wrap Character** property to configure, for the entire schema, the character used to wrap one or more characters so that they will be interpreted as simple data, rather than as having the special meaning they have otherwise been assigned.

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

## Category

Flat File

## Allowed Values

Either:

  - No value, resulting in no corresponding annotation in the XSD representation of the schema. This value is only allowed when the [Default Wrap Character Type](default-wrap-character-type-node-property-of-flat-file-schemas.md) property is set to **None**.

  - Any of the predefined character choices in the drop-down list.

  - Any other single character entered in the format indicated by your choice for the **Default Wrap Character Type** property.

## Default Value

No value, resulting in no annotation being added to the XSD representation of the schema.

## XSD Persistence

As the value of the **default\_wrap\_char** attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.

You must configure the **Default Wrap Character Type** property as **Character** or **Hexadecimal** before you can configure this property.

You can override the global setting established by this property by setting the [Wrap Character](wrap-character-node-property-of-flat-file-schemas.md) property for individual **Field Element** and **Field Attribute** nodes.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

