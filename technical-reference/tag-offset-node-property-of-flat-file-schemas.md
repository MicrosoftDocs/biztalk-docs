---
title: Tag Offset (Node Property of Flat File Schemas)
TOCTitle: Tag Offset (Node Property of Flat File Schemas)
ms:assetid: 82d7f1a0-5fe4-41d4-958d-81a9d2560f12
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561122(v=BTS.80)
ms:contentKeyID: 51529334
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Tag Offset (Node Property of Flat File Schemas)

 

Use the **Tag Offset** property to specify the starting offset of the tag within the positional record, starting from the beginning of that record. This also means that the tag must fit the positional record and can span more than one field in that record.

## Applies to Nodes of Type

[Record](record-node-properties.md)

## Category

Flat File

## Allowed Values

Non-negative integers.

## Default Value

None.

## XSD Persistence

As the value of the **tag\_offset** attribute of the **element/annotation/appinfo/recordInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor and you have:

  - Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node

  - Set the **Structure** property of the selected **Record** node to **Positional**

  - Set a value for the [Tag Identifier](tag-identifier-node-property-of-flat-file-schemas.md) property of the selected **Record** node

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

