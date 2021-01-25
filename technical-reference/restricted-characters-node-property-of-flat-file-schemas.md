---
description: "Learn more about: Restricted Characters (Node Property of Flat File Schemas)"
title: Restricted Characters (Node Property of Flat File Schemas)
TOCTitle: Restricted Characters (Node Property of Flat File Schemas)
ms:assetid: 854422a3-49c9-4a2e-81b2-f62e38886491
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561171(v=BTS.80)
ms:contentKeyID: 51529404
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Restricted Characters (Node Property of Flat File Schemas)

 

Use the **Restricted Characters** property to define ranges of characters that are restricted in instance messages.

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

## Category

Flat File

## Allowed Values

A set of zero or more non-overlapping character ranges, as configured in the **Restricted Characters** dialog box.

## Default Value

No restricted character ranges.

## XSD Persistence

Each restricted character range is persisted as the values of the **start** and **end** attributes of a **schema/annotation/appinfo/schemaInfo/restrictedCharacterRanges/interval** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.

Click the ellipsis (**...**) button located to the right of the value field for this property to open the **Restricted Characters** dialog box. In this dialog box, specify one or more ranges of restricted characters.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

