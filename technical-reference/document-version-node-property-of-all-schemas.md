---
description: "Learn more about: Document Version (Node Property of All Schemas)"
title: Document Version (Node Property of All Schemas)
TOCTitle: Document Version (Node Property of All Schemas)
ms:assetid: ead7746a-5e7d-4cfd-b755-54327928d710
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561732(v=BTS.80)
ms:contentKeyID: 51533182
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Document Version (Node Property of All Schemas)

 

Use the **Document Version** property to specify the version of the schema that you are configuring, using whatever versioning scheme makes sense for your business.

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

## Category

Reference

## Allowed Values

Any string allowed in XML.

## Default Value

None.

## XSD Persistence

As the value of the **version** attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor.

This value will be used as the version number of instance messages.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)  
[Document Type (Node Property of All Schemas)](document-type-node-property-of-all-schemas.md)

