---
title: Derivation Type (Node Property of All Schemas)
TOCTitle: Derivation Type (Node Property of All Schemas)
ms:assetid: 3d6ac9be-781d-45cf-928c-916628f105bf
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559718(v=BTS.80)
ms:contentKeyID: 51527458
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Derivation Type (Node Property of All Schemas)

 

Use the **Derivation Type** property to examine either the base complex type, or one of the derived complex types associated with the selected child node of an **Equivalent** node.

## Applies to Nodes of Type

[Equivalent Child](equivalent-child-node-properties.md)

## Category

General

## Read-Only Value

Either the base complex type or one of the derived complex types associated with the **Equivalent** node that is the parent of the selected node.

## XSD Persistence

None. The child nodes of the **Equivalent** node and their properties exist to display the type derivations occurring within the XSD, but have no direct XSD persistence. The values of the **Base Data Type** and **Data Structure Type** properties of the associated nodes can be viewed as a form of indirect XSD persistence.

## Remarks

You can examine this property in the Visual Studio Properties window when you select a named node that is a child of an **Equivalent** node in BizTalk Editor.

The number of child nodes for a given **Equivalent** node will equal the number of derived complex types plus one (for the base complex type), and the value of this property will be set to one of these different possible values.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

