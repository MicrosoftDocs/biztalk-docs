---
description: "Learn more about: Group Reference (Node Property of All Schemas)"
title: Group Reference (Node Property of All Schemas)
TOCTitle: Group Reference (Node Property of All Schemas)
ms:assetid: 62919e8b-f312-4ff0-97ea-53bd0e6ece28
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560477(v=BTS.80)
ms:contentKeyID: 51528478
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Group Reference (Node Property of All Schemas)

 

Use the **Group Reference** property to specify a name for the globally defined group referenced by the selected **Sequence Group**, **Choice Group**, **All Group**, or **Attribute Group** node.

**Attribute Group** nodes are inherently global, and therefore are given default **Group Reference** property values. You can change this default name to another name but you cannot change it to an empty string.

**Sequence Group**, **Choice Group**, and **All Group** nodes are not global by default, and therefore are not given default **Group Reference** property values when they are first inserted into a schema. If you provide a value for the **Group Reference** property of one of these element groups, either an existing value or a new unique value, you are effectively choosing to reference an existing global element group or converting the element group into a global element group, respectively.

## Applies to Nodes of Type

[Sequence Group](sequence-group-node-properties.md), [Choice Group](choice-group-node-properties.md), [All Group](all-group-node-properties.md), [Attribute Group](attribute-group-node-properties.md)

## Category

Advanced

## Allowed Values

A blank value, which is not allowed for **Attribute Group** nodes, means that the element group is "inbuilt" and "unnamed". It has no name and cannot be used by other element groups. If you change a blank value to a brand new value, the name of the group is changed to the new value and it is moved to the global scope. If you change a blank value to an existing group name, you are reusing the chosen group at the selected location in the schema.

If there is a value, the group is declared globally and can be used by other element or attribute groups, as applicable. If you change from a value to another brand new value, the name of the group is changed to the new value. If you change from a value to an existing group name, you are reusing that group at the selected location in the schema.

## Default Value

For **Attribute Group** nodes, the default value upon node insertion is of the form "AttrGroup*N*", where "*N*" is a monotonically increasing number starting with zero.

For **Sequence Group**, **Choice Group**, and **All Group** nodes, the default value upon node insertion is blank, meaning that the element group is not global.

## XSD Persistence

As the values of the **name** and **ref** attributes of pairs of either **group** or **attributeGroup** elements. The **group** or **attributeGroup** element that appears at the global level of the schema has its **name** attribute set to the value of the **Group Reference** property, and the **group** or **attributeGroup** element that appears deeper in the schema hierarchy has its **ref** attribute set to the same value, thereby establishing the reference.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Sequence Group**, **Choice Group**, **All Group**, or **Attribute Group** node in BizTalk Editor.

This property represents an XSD concept related to the **group** and **attributeGroup** elements.

The value of the **Group Reference** property, if any, appears as the second half of the [Node Name](node-name-node-property-of-all-schemas.md) property of the selected group node, as follows:

  - For **Attribute Group** nodes:
    
    \<AttrGroup:*GroupReferencePropertyValue*\>

  - For **Sequence Group**, **Choice Group**, and **All Group** nodes:
    
    \<Group:*GroupReferencePropertyValue*\>

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

