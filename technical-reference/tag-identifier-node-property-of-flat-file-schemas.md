---
title: Tag Identifier (Node Property of Flat File Schemas)
TOCTitle: Tag Identifier (Node Property of Flat File Schemas)
ms:assetid: 3e37e433-e69c-47ce-b257-190cac7b80ae
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559732(v=BTS.80)
ms:contentKeyID: 51527538
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Tag Identifier (Node Property of Flat File Schemas)

 

Use the **Tag Identifier** property to specify an identifying tag for a non-XML record.

## Applies to Nodes of Type

[Record](record-node-properties.md)

## Category

Flat File

## Allowed Values

Any string that is valid in XML.

## Default Value

None.

## XSD Persistence

As the value of the **tag\_name** attribute of the **element/annotation/appinfo/recordInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)  
[Tag Offset (Node Property of Flat File Schemas)](tag-offset-node-property-of-flat-file-schemas.md)

