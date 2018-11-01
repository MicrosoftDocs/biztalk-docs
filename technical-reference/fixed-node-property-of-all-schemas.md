---
title: Fixed (Node Property of All Schemas)
TOCTitle: Fixed (Node Property of All Schemas)
ms:assetid: 4edfb40c-6401-4f78-9851-119904d4b4c9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560089(v=BTS.80)
ms:contentKeyID: 51527939
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Fixed (Node Property of All Schemas)

 

Use the **Fixed** property to specify a fixed value for the corresponding element or attribute in an instance message; if the corresponding element or attribute is present in an instance message, it must have the specified "fixed" value in order to be valid.

## Applies to Nodes of Type

[Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

## Category

Advanced

## Allowed Values

Any value that conforms to the data type specified by the **Data Type** property.

## Default Value

None.

## XSD Persistence

The value of this property, if any, is used as the value of the **fixed** attribute of the element that corresponds to the selected **Field Element** or **Field Attribute** node.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Field Element** node in BizTalk Editor.

This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](https://msdn.microsoft.com/en-us/library/aa547363\(v=bts.80\)).

You cannot configure both the **Fixed** and **Default Value** properties because it is prohibited by XSD.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

