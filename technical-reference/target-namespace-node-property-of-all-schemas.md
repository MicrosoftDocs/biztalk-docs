---
title: Target Namespace (Node Property of All Schemas)
TOCTitle: Target Namespace (Node Property of All Schemas)
ms:assetid: 6067d3a3-f8f4-4ba4-b6c3-175755b90d67
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560441(v=BTS.80)
ms:contentKeyID: 51528429
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Target Namespace (Node Property of All Schemas)

 

Use the **Target Namespace** property to configure the target namespace for the schema using any valid uniform resource identifier (URI).

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

## Category

General

## Allowed Values

Any valid URI.

## Default Value

http://*ProjectName*.*SchemaName*, where "*ProjectName*" is the name of the project in which the schema was created and "*SchemaName*" is the name of the schema (without the XSD file extension. If either the project name or the schema name contains spaces, they are replaced with underscore (\_) characters. For example, if the project name is "BizTalk Server Project2" and the schema name is "Project 3", the default target namespace value will be:

http://BizTalk\_Server\_Project2.Schema\_3

## XSD Persistence

As the value of the **targetNamespace** attribute of the **schema** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Schema** node in BizTalk Editor.

This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

If you use "x-schema" in the **targetNamespace** attribute value, you may cause a test failure when you test the instance in BizTalk Mapper.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

