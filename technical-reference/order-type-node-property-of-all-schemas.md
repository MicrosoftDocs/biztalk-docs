---
title: Order Type (Node Property of All Schemas)
TOCTitle: Order Type (Node Property of All Schemas)
ms:assetid: c08082e1-4ee8-4b13-90d8-ec920b95eda5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578439(v=BTS.80)
ms:contentKeyID: 51530928
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Order Type (Node Property of All Schemas)

 

Use the **Order Type** property to change the type of the selected element group node. For example, you can change a **Sequence Group** node to a **Choice Group** node, and vice versa. This will also change the node name in the schema tree view from "\<Sequence\>" to "\<Choice\>" (or vice versa).

## Applies to Nodes of Type

[Sequence Group](sequence-group-node-properties.md), [Choice Group](choice-group-node-properties.md), [All Group](all-group-node-properties.md)

## Category

Advanced

## Allowed Values

<table>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Sequence</strong></td>
<td>Specifies that the elements within the selected group node must appear in the same order as they are defined in the schema.</td>
</tr>
<tr class="even">
<td><strong>Choice</strong></td>
<td>Specifies that an instance message must not contain more than one of the elements defined within the selected group node in the schema.</td>
</tr>
<tr class="odd">
<td><strong>All</strong></td>
<td>Specifies that all of the elements within the selected group node may appear once or not at all, and they may appear in any order. <strong>Note:</strong> You can use <strong>All Group</strong> nodes only in relation to inheritance; they cannot generally be inserted directly into a schema. See remarks for additional information.</td>
</tr>
</tbody>
</table>


## Default Value

The default value of this property corresponds to the type of element group node that you insert: **Sequence** for **Sequence Group** nodes and **Choice** for **Choice Group** nodes, and **All** for **All Group** nodes.

## XSD Persistence

As a **sequence**, **choice**, or **all** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Sequence Group**, **Choice Group**, or **All Group** node in BizTalk Editor. There are circumstances where the structure or hierarchy placement of an element group node prevents it from being switched from one type of element group node to another.

When you change the value of this property from **Sequence** or **Choice** to **All**, the values of the **Min Occurs** and **Max Occurs** properties are automatically set to one (1).

This property can be useful when you have an element group node with a large number of children and find that the element group should be of a different kind. Rather than recreating the group and all of its children, you can simply change the value of this property to achieve the same effect.

This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

The **All Group** node has a number of special restrictions to which the **Sequence Group** and **Choice Group** nodes are not subject:

  - **All Group** nodes cannot be the child of any group element node.

  - The **Content Type** property of the parent **Record** node must be set to **ComplexContent**.

  - An **All Group** node must be the first group node within its parent **Record** node.

  - **All Group** nodes cannot contain other groups: sequence , choice, or all.

  - Child element nodes (**Record** and **Field Element** nodes) must have their **Max Occurs** properties set to one (1).

Whenever you insert a **Record** node and start inserting nodes within it, a hidden sequence group is always created by default immediately under that **Record** node. This default group order type can be changed using the **Group Order Type** property of the **Record** node. Because an **All Group** node cannot occur within any other group node, and because of the use of a hidden sequence group, you cannot insert an **All Group** node within a **Record** node in BizTalk Editor.

In case of inheritance, we are forced to show the top-level group node because, the base complex type can have one **Order Type** property value setting (say, **Sequence**) and the derived complex type can have a different value (say, **All**). An element that is using the derived complex type is going to have the content model of the base complex type and the content model of the derived complex type. Because these two content models can be different (for example, one is a sequence group and the other is an all group), we have to show these group nodes explicitly.

However, there is one exceptional case in which you can directly insert an **All Group** node and directly modify its properties. When complex type inheritance is used in a schema, BizTalk Editor exposes the top-level group node, and therefore allows insertion, deletion, and modification of an **All Group** node.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

