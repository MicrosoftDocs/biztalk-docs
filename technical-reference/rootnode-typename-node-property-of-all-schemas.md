---
title: RootNode TypeName (Node Property of All Schemas)
TOCTitle: RootNode TypeName (Node Property of All Schemas)
ms:assetid: fa10f0bf-da9c-4709-b308-6466213e4bf2
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa562051(v=BTS.80)
ms:contentKeyID: 51533559
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# RootNode TypeName (Node Property of All Schemas)

 

Use the **RootNode TypeName** property to specify an alternative name (other than the value of the **Node Name** property of the root node) to use when generating the .NET class name for the selected root **Record** or **Field Element** node.

## Applies to Nodes of Type

[Record](record-node-properties.md), [Field Element](field-element-node-properties.md)

(Root nodes only.)

## Category

Reference

## Allowed Values

Valid C\# class names, which excludes C\# reserved words.

## Default Value

The value of the **Node Name** property of the selected root node.

## XSD Persistence

As the value of the **rootTypeName** attribute of the **element/annotation/appinfo/recordInfo** element that corresponds to a root **Record** node.

Or as the value of the **rootTypeName** attribute of the **element/annotation/appinfo/fieldInfo** element that corresponds to a root **Field Element** node.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a top-level (root) **Record** or **Field Element** node in BizTalk Editor.

Because the period (.) character has a special meaning in C\#, avoid using it in values for this property.

Unless the **Root Reference** property of the **Schema** node is set, every top-level **Record** and **Field Element** root node in the schema gets compiled into a .NET class in the BizTalk assembly for the project using the values of the **Node Name** properties of those root nodes as the C\# class names. The set of valid **Node Name** property values is larger than the set of valid C\# class names, due to reserved words in C\# and so on. There may be occasions where it is not reasonable to change the **Node Name** property value to accommodate this requirement of the compilation process, such as when a **Node Name** property value and the resulting instance message element name have already been agreed upon with a trading partner. The **RootNode TypeName** property provides a way to provide a different name for the C\# class name associated with a particular root node. By default, the **RootNode TypeName** property is set to the value of the **Node Name** property. If you encounter a compilation problem related to the C\# class name not being valid, you can change the value of the **RootNode TypeName** property to change the name of the generated C\# class without disrupting the **Node Name** property value and the corresponding element name in instance messages.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

