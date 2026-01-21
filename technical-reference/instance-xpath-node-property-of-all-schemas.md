---
description: "Learn more about: Instance XPath (Node Property of All Schemas)"
title: Instance XPath (Node Property of All Schemas)
TOCTitle: Instance XPath (Node Property of All Schemas)
ms:assetid: 46464980-8e70-4c8e-bf71-5b9fa3094807
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559880(v=BTS.80)
ms:contentKeyID: 51527735
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Instance XPath (Node Property of All Schemas)

Â 

Use the **Instance XPath** property to view the XPath of the element or attribute associated with the selected node in an instance message.

## Applies to Nodes of Type

[Record](record-node-properties.md), [Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md), [Any Element](any-element-node-properties.md), [Any Attribute](any-attribute-node-properties.md)

## Category

General

## Read-Only Value

The XPath of the element or attribute associated with the selected node in an instance message.

## XSD Persistence

Implicit in the structure of the XSD.

## Remarks

You can examine this property in the Visual Studio Properties window when you select a node of an appropriate type (including a root **Record** node) in BizTalk Editor.

This property is read-only; however, you can copy this value and paste it to another location.

When you examine the **Instance XPath** property for **Any Element** and **Any Attribute** nodes, you will see one of the substrings "\<Any\>" or "\<AnyAttribute\>", respectively, in the property value string. These elements appear in the property value strings as wildcard placeholders in the positions of whatever element(s) or attribute(s), respectively, actually occur in a corresponding instance message. Actual elements named "Any" or attributes named "AnyAttribute" are not likely to occur in instance messages.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)


