---
description: "Learn more about: Child Delimiter (Node Property of Flat File Schemas)"
title: Child Delimiter (Node Property of Flat File Schemas)
TOCTitle: Child Delimiter (Node Property of Flat File Schemas)
ms:assetid: 623841ac-925d-42af-8476-28493e4c804f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560472(v=BTS.80)
ms:contentKeyID: 51528458
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Child Delimiter (Node Property of Flat File Schemas)

 

Use the **Child Delimiter** property to configure, on a per-record basis, the string used to delimit fields in this record in instance data.

## Applies to Nodes of Type

[Record](record-node-properties.md)

## Category

Flat File

## Allowed Values

Either:

  - No value, resulting in no annotation being added to the XSD representation of the schema.

  - Any string of characters entered in the format indicated by your choice for the [Child Delimiter Type](child-delimiter-type-node-property-of-flat-file-schemas.md) property.

## Default Value

No value, resulting in no annotation being added to the XSD representation of the schema.

## XSD Persistence

As the value of the **child\_delimiter** attribute of the **element/annotation/appinfo/recordInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you have:

  - Selected a **Record** node (including a root **Record** node) in BizTalk Editor

  - Set the **Structure** property of the selected **Record** node to **Delimited**

  - Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node

The maximum length of the child delimiter string is 100 characters.

You must configure the **Child Delimiter Type** property as **Character** or **Hexadecimal** before you can configure this property.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

