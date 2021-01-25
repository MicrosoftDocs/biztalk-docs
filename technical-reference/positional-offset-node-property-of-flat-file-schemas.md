---
description: "Learn more about: Positional Offset (Node Property of Flat File Schemas)"
title: Positional Offset (Node Property of Flat File Schemas)
TOCTitle: Positional Offset (Node Property of Flat File Schemas)
ms:assetid: 1ad10153-01e4-411b-a54c-5c6decc3a6a3
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559049(v=BTS.80)
ms:contentKeyID: 51526575
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Positional Offset (Node Property of Flat File Schemas)

 

Use the **Positional Offset** property to configure the starting offset of the field relative to the previous sibling or delimiter.

## Applies to Nodes of Type

[Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

## Category

Reference

## Allowed Values

Either:

  - No value, resulting in no corresponding annotation in the XSD representation of the schema, and specifying that the default value of zero (0) will be used.

  - A non-negative integer, indicating the starting offset, relative to the previous sibling or delimiter, of the corresponding field in instance messages.

## Default Value

No value, resulting in no corresponding annotation in the XSD representation of the schema, and specifying that the default value of zero (0) will be used.

## XSD Persistence

As the value of the **pos\_offset** attribute of:

  - For **Field Element** nodes, the **element/annotation/appinfo/fieldInfo** annotation element.

  - For **Field Attribute** nodes, the **attribute/annotation/appinfo/fieldInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have:

  - Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node

  - Set the **Structure** property of the containing **Record** node to **Positional**

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

