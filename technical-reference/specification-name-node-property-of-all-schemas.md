---
title: Specification Name (Node Property of All Schemas)
TOCTitle: Specification Name (Node Property of All Schemas)
ms:assetid: 4260e1df-d6a4-49d0-a5ae-321f59e78f89
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559802(v=BTS.80)
ms:contentKeyID: 51527621
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Specification Name (Node Property of All Schemas)

 

Use the **Specification Name** property to designate a business name for the schema.

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

## Category

Reference

## Allowed Values

Any string allowed in XML.

## Default Value

None.

## XSD Persistence

As the value of the **schema\_name** attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Schema** node in BizTalk Editor.

An example of setting this property is when you are creating a purchase order that you use exclusively with your supply chain management process, you might enter a value of "Supply Change PO" for this property.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

