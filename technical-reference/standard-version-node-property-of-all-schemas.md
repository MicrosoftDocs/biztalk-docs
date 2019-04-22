---
title: Standard Version (Node Property of All Schemas)
TOCTitle: Standard Version (Node Property of All Schemas)
ms:assetid: bb9c08b2-8cf1-4263-acaf-861c58f33c22
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578346(v=BTS.80)
ms:contentKeyID: 51530839
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Standard Version (Node Property of All Schemas)

 

Use the **Standard Version** property to qualify the version of the instance message format and/or syntax that you established using the [Standard](standard-node-property-of-all-schemas.md) property, if appropriate.

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

## Category

Reference

## Allowed Values

Any string, although it is most often a version string of some sort that is associated with the value set for the **Standard** property.

## Default Value

None.

## XSD Persistence

As the value of the **standards\_version** attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Schema** node in BizTalk Editor.

An example of setting this property is when the standard is X12, you might set this property to "004010", or if the standard is EDIFACT, you might set this property to "D97B".

If you intend to use the CodeList feature, you should avoid using the period character (".") in the string you provide for this property. For additional information about this restriction, see [CodeList (Node Property of All Schemas)](codelist-node-property-of-all-schemas.md) and [CodeList Database (Node Property of All Schemas)](codelist-database-node-property-of-all-schemas.md).

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

