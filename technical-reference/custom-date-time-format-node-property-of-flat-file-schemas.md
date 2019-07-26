---
title: Custom Date-Time Format (Node Property of Flat File Schemas)
TOCTitle: Custom Date-Time Format (Node Property of Flat File Schemas)
ms:assetid: 83d3e688-40bc-4547-9ef1-c0f0554201df
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561142(v=BTS.80)
ms:contentKeyID: 51529363
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Custom Date-Time Format (Node Property of Flat File Schemas)

 

Use the **Custom Date/Time Format** property to configure the date/time format found in the flat files for which this schema defines the structure.

## Applies to Nodes of Type

[Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

## Category

Flat File

## Allowed Values

You can configure this property with almost any time and date format, except for Julian dates. The drop-down list provides various choices, but you can also type a different format of your choosing.

Allowable separators include dash (-), slash (/), and period (.).

## Default Value

No value, resulting in no annotation being added to the XSD representation of the schema.

## XSD Persistence

As the value of the **datetime\_format** attribute of the **fieldInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you have:

  - Selected a **Field Element** or **Field Attribute** node in BizTalk Editor

  - Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node

  - Set the data type of the selected **Field Element** or **Field Attribute** node to a date, time, or date/time type

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

