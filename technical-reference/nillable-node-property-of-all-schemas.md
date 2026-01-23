---
description: "Learn more about: Nillable (Node Property of All Schemas)"
title: Nillable (Node Property of All Schemas)
TOCTitle: Nillable (Node Property of All Schemas)
ms:assetid: ca6f2282-de14-45cf-8672-191df723fd97
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547995(v=BTS.80)
ms:contentKeyID: 51531305
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Nillable (Node Property of All Schemas) 

Use the **Nillable** property to specify whether the **nil** attribute can be used with the corresponding instance message element to indicate that it is still valid even if it has no content.

## Applies to Nodes of Type

[Record](record-node-properties.md), [Field Element](field-element-node-properties.md)

## Category

Advanced

## Allowed Values

- **True**: Sets the **nillable** attribute of the corresponding instance message element to "true", specifying that if the corresponding element in instance messages has a **nil** attribute with a value of "true", that element must not contain any data.
- **False**: Removes the **nillable** attribute of the corresponding instance message element, specifying that the **nil** attribute must not be used with the corresponding element in an instance message.

## Default Value

**False**, specifying that the **nil** attribute should not be used with the corresponding element or attribute in an instance message.

## XSD Persistence

As the value of the **nillable** attribute of the element that corresponds to the selected **Record** or **Field Element** node.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record** (including a root **Record** node) or **Field Element** node in BizTalk Editor.

This property represents a standard XSD construct. 

In instance messages, the use of the **nil** attribute must include the namespace prefix for the XML Schema namespace for instances, `https://www.w3.org/2001/XMLSchema-instance.xsd`, which is "xsi" by convention. An element in an instance message that includes the attribute setting **xsi:nil="true"** may not have any element content but it may still have attributes.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

