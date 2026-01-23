---
description: "Learn more about: Namespace (Node Property of All Schemas)"
title: Namespace (Node Property of All Schemas)
TOCTitle: Namespace (Node Property of All Schemas)
ms:assetid: b4a430b0-aeab-463e-af8c-5e9d351a57bd
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578213(v=BTS.80)
ms:contentKeyID: 51530636
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Namespace (Node Property of All Schemas)

 

Use the **Namespace** property to examine and, for **Any Element** and **Any Attribute** nodes, set the namespace for the selected node, if any.

## Applies to Nodes of Type

[Record](record-node-properties.md), [Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md), [Sequence Group](sequence-group-node-properties.md), [Choice Group](choice-group-node-properties.md), [All Group](all-group-node-properties.md), [Attribute Group](attribute-group-node-properties.md), [Any Element](any-element-node-properties.md), [Any Attribute](any-attribute-node-properties.md)

## Category

General

## Allowed Values

Any valid URI.

## Default Value

None.

## XSD Persistence

As the value of the prefix on the element name from among the imported namespace prefixes, or as the **namespace** attribute of an **any** or **anyAttribute** element.

## Remarks

You can examine this property in the Visual Studio Properties window when you select a node of an appropriate type (including a root **Record** node) in BizTalk Editor.

This property is read-only for all node types other than **Any Element** and **Any Attribute**.

When the **Namespace** property is blank, it means that the selected node is in the "blank" namespace. For example, when you define a schema with no value set for its **Target Namespace** property, all of the nodes in that schema are in the blank namespace.

This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

