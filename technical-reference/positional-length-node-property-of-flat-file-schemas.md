---
description: "Learn more about: Positional Length (Node Property of Flat File Schemas)"
title: Positional Length (Node Property of Flat File Schemas)
TOCTitle: Positional Length (Node Property of Flat File Schemas)
ms:assetid: 8b3131d4-b8b1-4501-ae94-52de93561bac
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561278(v=BTS.80)
ms:contentKeyID: 51529553
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
---

# Positional Length (Node Property of Flat File Schemas)

 

Use the **Positional Length** property to configure the field length from the previous sibling or delimiter.

## Applies to Nodes of Type

[Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

## Category

Reference

## Allowed Values

A non-negative integer, indicating the length of the corresponding field in instance messages.

## Default Value

No value, resulting in no corresponding annotation in the XSD representation of the schema.

## XSD Persistence

As the value of the **pos\_length** attribute of:

  - For **Field Element** nodes, the **element/annotation/appinfo/fieldInfo** annotation element.

  - For **Field Attribute** nodes, the **attribute/annotation/appinfo/fieldInfo** annotation element.

## Remarks

You can examine this property in the Visual Studio Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have:

  - Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node

  - Set the **Structure** property of the containing **Record** node to **Positional**

You must set a value for this property when you have set the **Structure** property of the containing **Record** node to **Positional**.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

