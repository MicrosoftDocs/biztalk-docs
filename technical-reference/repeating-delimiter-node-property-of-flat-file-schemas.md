---
description: "Learn more about: Repeating Delimiter (Node Property of Flat File Schemas)"
title: Repeating Delimiter (Node Property of Flat File Schemas)
TOCTitle: Repeating Delimiter (Node Property of Flat File Schemas)
ms:assetid: 8d3209ad-a25c-48c6-855c-96dbbb7e32d8
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561309(v=BTS.80)
ms:contentKeyID: 51529598
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Repeating Delimiter (Node Property of Flat File Schemas)

 

Use the **Repeating Delimiter** property to configure, on a per-record basis, the string used to delimit repeating fields in this record in instance data.

## Applies to Nodes of Type

[Record](record-node-properties.md)

## Category

Flat File

## Allowed Values

Either:

  - No value, resulting in no annotation being added to the XSD representation of the schema, and specifying that the child delimiter specified for the selected **Record** node will be used. This value is only allowed when the [Repeating Delimiter Type](repeating-delimiter-type-node-property-of-flat-file-schemas.md) property is set to **None**.

  - Any string of characters entered in the format indicated by your choice for the **Repeating Delimiter Type** property.

## Default Value

No value, resulting in no annotation being added to the XSD representation of the schema, and specifying that the child delimiter specified for the selected **Record** node will be used.

## XSD Persistence

As the value of the **repeating\_delimiter** attribute of the **element/annotation/appInfo/recordInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor and you have:

  - Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node

  - Set the **Structure** property of the selected **Record** node to **Delimited**

You must configure the **Repeating Delimiter Type** property as **Character** or **Hexadecimal** before you can configure this property.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

