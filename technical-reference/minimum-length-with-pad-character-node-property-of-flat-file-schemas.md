---
description: "Learn more about: Minimum Length with Pad Character (Node Property of Flat File Schemas)"
title: Minimum Length with Pad Character (Node Property of Flat File Schemas)
TOCTitle: Minimum Length with Pad Character (Node Property of Flat File Schemas)
ms:assetid: 0a2dbfb2-4956-44f1-a67c-56ef1e7ad29c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547122(v=BTS.80)
ms:contentKeyID: 51526106
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Minimum Length with Pad Character (Node Property of Flat File Schemas)

 

Use the **Minimum Length with Pad Character** property to configure how a serializer pads the instance message data associated with the selected **Field Element** or **Field Attribute** node.

## Applies to Nodes of Type

[Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

## Category

Flat File

## Allowed Values

No value, resulting in no annotation being added to the XSD representation of the schema and no padding being performed, or a positive integer indicating the minimum length to which the field associated with the selected **Field Element** or **Field Attribute** node should be padded.

## Default Value

No value, resulting in no annotation being added to the XSD representation of the schema and no padding being performed.

## XSD Persistence

As the value of the **min\_length\_with\_pad** attribute of:

  - For **Field Element** nodes, the **element/annotation/appinfo/fieldInfo** annotation element.

  - For **Field Attribute** nodes, the **attribute/annotation/appinfo/fieldInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have:

  - Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node

  - Set the **Structure** property of the containing **Record** node to **Delimited**

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

