---
description: "Learn more about: Default Value (Node Property of All Schemas)"
title: Default Value (Node Property of All Schemas)
TOCTitle: Default Value (Node Property of All Schemas)
ms:assetid: 32fe94f4-7e71-456e-b55e-91a28e4a762c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559513(v=BTS.80)
ms:contentKeyID: 51527192
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Default Value (Node Property of All Schemas)

 

Use the **Default Value** property to specify the default value for the message instance field that corresponds to the selected **Field Element** or **Field Attribute** node.

## Applies to Nodes of Type

[Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

## Category

General

## Allowed Values

Any value that conforms to the data type specified by the [Data Type](data-type-node-property-of-all-schemas.md) property.

## Default Value

None.

## XSD Persistence

As the value of the **default** attribute of the element that corresponds to the selected **Field Element** or **Field Attribute** node.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor.

You can configure this property with any valid XML data that is of the associated simple type.


> [!NOTE]
> <P>Date and time data types, of which there are several, must conform to ISO 8601 formats. In brief, dates are expressed as <STRONG>YYYY-MM-DD</STRONG> and hours are expressed as <STRONG>hh:mm:ss</STRONG> using 24-hour notation. When they occur together, date and time values are separated by the "T" character: <STRONG>YYYY:MM:DDThh:mm:ss</STRONG>.</P>



This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

You cannot configure both the **Default Value** property and the **Fixed** property because it is prohibited by XSD.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

