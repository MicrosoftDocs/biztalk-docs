---
title: Base Data Type (Node Property of All Schemas)
TOCTitle: Base Data Type (Node Property of All Schemas)
ms:assetid: 17972a21-fe2e-4968-ab94-89f87d6b93f6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa558779(v=BTS.80)
ms:contentKeyID: 51526470
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Base Data Type (Node Property of All Schemas)

 

Use the **Base Data Type** property to specify the base data type value from which the data type of the selected **Record**, **Field Element**, or **Field Attribute** node will be derived (for example, "xs:string").

## Applies to Nodes of Type

[Record](record-node-properties.md), [Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

## Category

Advanced

## Allowed Values

No value, or any of the data types shown in the drop-down list for this property.

## Default Value

Blank, indicating that the data type of this **Record**, **Field Element**, or **Field Attribute** node is not derived from another data type.

## XSD Persistence

As the value of the **base** attribute of the **extension**, **restriction**, **list**, or **union** element within the element(s) that corresponds to the selected **Record**, **Field Element**,or **Field Attribute** node. For more information about the persistence permutations, see the XSD Persistence section of [Derived By (Node Property of All Schemas)](derived-by-node-property-of-all-schemas.md).

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record** (including a root **Record** node), **Field Element**, or **Field Attribute** node in BizTalk Editor.

The setting of this property interacts with the [Content Type](content-type-node-property-of-all-schemas.md) (**Record** nodes only) and [Derived By](derived-by-node-property-of-all-schemas.md) properties.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

