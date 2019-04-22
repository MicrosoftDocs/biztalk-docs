---
title: Pattern (Node Property of All Schemas)
TOCTitle: Pattern (Node Property of All Schemas)
ms:assetid: 86dec810-b972-48d9-8141-3f07e3a3035e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561200(v=BTS.80)
ms:contentKeyID: 51529444
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Pattern (Node Property of All Schemas)

 

Use the **Pattern** property to limit any data in an instance message corresponding to the selected **Field Element** or **Field Attribute** node to a specific pattern, as specified by one or more regular expressions.

## Applies to Nodes of Type

[Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

## Category

Restricted

## Allowed Values

One or more regular expressions that are valid for the data type of the selected **Field Element** or **Field Attribute** node.

## Default Value

None.

## XSD Persistence

As a **pattern** element and its **value** attribute for each regular expression specified for this property.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have set its **Derived By** property to **Restriction**.

This property represents an XSD concept related to the **simpleType** element and its **restriction** subelement.

You can create patterns by clicking the ellipsis (**...**) button located to the right of the **Pattern** property value field to open the **Pattern Editor** dialog box. In this dialog box, you can type the regular expressions for your patterns, one per line, into a multi-line edit box labeled **Values**.

Each of the regular expressions you provide must be valid with respect to the specified data type of the selected **Field Element** or **Field Attribute** node. Some pattern problems are detected immediately; others can result in run-time errors.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

