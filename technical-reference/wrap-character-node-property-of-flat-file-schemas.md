---
title: Wrap Character (Node Property of Flat File Schemas)
TOCTitle: Wrap Character (Node Property of Flat File Schemas)
ms:assetid: 7a3aa9f6-cc7c-4837-90d1-66ee52361435
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560939(v=BTS.80)
ms:contentKeyID: 51529098
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Wrap Character (Node Property of Flat File Schemas)

 

Use the **Wrap Character** property to configure, on a per-field basis, the character used to wrap one or more characters so that they will be interpreted as simple data, rather than as having the special meaning they have otherwise been assigned.

## Applies to Nodes of Type

[Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

## Category

Flat File

## Allowed Values

Either:

  - No value, resulting in no corresponding annotation in the XSD representation of the schema, and specifying that there is no wrap character defined for the selected **Field Element** or **Field Attribute** node. This value is only allowed when the [Wrap Character Type](wrap-character-type-node-property-of-flat-file-schemas.md) property is set to **None**.

  - Any of the predefined character choices in the drop-down list.

  - Any other single character entered in the format indicated by your choice for the **Wrap Character Type** property.

## Default Value

No value, resulting in no corresponding annotation in the XSD representation of the schema.

## XSD Persistence

As the value of the **wrap\_char** attribute of:

  - For **Field Element** nodes, the **element/annotation/appinfo/fieldInfo** annotation element.

  - For **Field Attribute** nodes, the **attribute/annotation/appinfo/fieldInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have:

  - Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node

  - Set the **Structure** property of the containing **Record** node to **Delimited**

You must configure the **Wrap Character Type** property as **Character** or **Hexadecimal** before you can configure this property.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)  
[Default Wrap Character (Node Property of Flat File Schemas)](default-wrap-character-node-property-of-flat-file-schemas.md)

