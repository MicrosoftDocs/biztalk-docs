---
title: Namespace (Schema Item Property)
TOCTitle: Namespace (Schema Item Property)
ms:assetid: 750a8260-1cfb-4997-b8ed-b62359d40fc3
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560842(v=BTS.80)
ms:contentKeyID: 51528973
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Namespace (Schema Item Property)

 

Use the **Namespace** property to specify the .NET namespace of the managed type associated with the selected schema file.

## Category

Advanced

## Allowed Values

Any valid .NET namespace string that is not reserved in C\# or by BizTalk Server and is different than the value you have set for the **Type Name** property.

## Default Value

The BizTalk project name, with space characters replaced by underscore characters.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a schema file in Solution Explorer.

When you compile a schema, BizTalk Server automatically creates a number of C\# classes within the namespace specified by this property. This includes classes for every document schema and at least one, but possibly all, root nodes in the document schemas. Further, BizTalk Server creates a C\# class for every property schema and for every property declared in such schemas. This creates the potential for class name clashes during schema compilation. The values of the following properties can be used for automatically generated class names, depending on circumstances such as whether the schema has a single root node or multiple root nodes:

  - **Type Name** property of the **Schema** node

  - **Name** property of root nodes in document schemas

  - **RootNode TypeName** property of root nodes in document schemas

  - **Name** property of (root) **Field Element** nodes in property schemas

Within a given namespace, you need to observe the following rules for the values of these properties:

  - They should be unique.

  - They should not be set to a C\# reserved word, such as "string".

  - They should not include the period (.) character because of its special meaning in C\#.

  - They should not be the same as the value of the **Namespace** property of the corresponding **Schema** node.

Confirm to these rules by changing the namespace value and/or changing one or more of these other property values.

## See Also

[Type Name (Schema Item Property)](type-name-schema-item-property.md)  
[Fully Qualified Name (Schema Item Property)](fully-qualified-name-schema-item-property.md)

