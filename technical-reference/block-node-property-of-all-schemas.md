---
title: Block (Node Property of All Schemas)
TOCTitle: Block (Node Property of All Schemas)
ms:assetid: 068c9913-183e-452d-a66f-9b0a12f259d9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547049(v=BTS.80)
ms:contentKeyID: 51526008
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Block (Node Property of All Schemas)

 

Use the **Block** property to prevent or restrict the types of derivations that can be used in instance messages for the element(s) corresponding to the selected **Record** node.

## Applies to Nodes of Type

[Record](record-node-properties.md)

## Category

General

## Allowed Values

<table>
<thead>
<tr class="header">
<th>Drop-down list choice</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>(Default)</strong></td>
<td>Removes the <strong>block</strong> attribute, if present, specifying that there are no restrictions on particular types of derivations unless otherwise specified by the <a href="blockdefault-node-property-of-all-schemas.md">BlockDefault</a> property.</td>
</tr>
<tr class="even">
<td><strong>All</strong></td>
<td>Sets the <strong>block</strong> attribute to &quot;#all&quot;, specifying that no derivations are allowed.</td>
</tr>
<tr class="odd">
<td><strong>Restriction</strong></td>
<td>Adds &quot;restriction&quot; to the value of the <strong>block</strong> attribute, specifying that derivations by restriction are not allowed.</td>
</tr>
<tr class="even">
<td><strong>Extension</strong></td>
<td>Adds &quot;extension&quot; to the value of the <strong>block</strong> attribute, specifying that derivations by extension are not allowed.</td>
</tr>
<tr class="odd">
<td><strong>Substitution</strong></td>
<td>Adds &quot;substitution&quot; to the value of the <strong>block</strong> attribute, specifying that derivations by substitution are not allowed.</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**

## XSD Persistence

As the value of the **block** attribute of the **complexType** element that is a child of the element that corresponds to the selected **Record** node.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor.

This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

The values **Restriction**, **Extension**, and **Substitution** can be set in combination with each other by selecting their corresponding check boxes in the **Block** property drop-down list. The corresponding values of the **block** attribute are space-separated.

In corresponding instance messages, other derived data types can be used for a particular element unless explicitly prevented by the settings of the **Block** and/or **BlockDefault** properties, as follows:

```C#
<RecordName   
            xmlns:xsi="http://www.w3c.org/2001/XMLSchema-instance>"  
  
```

In the example above, "BaseOrDerivedTypeName" is the name of a complex type that is derived from the data type specified by the **Data Structure Type** property of the corresponding **Record** node by some allowed type of derivation (a type of derivation that is not blocked by this property or the **BlockDefault** property). For more information about different types of derivations, see [Type Reuse and Derivations](https://msdn.microsoft.com/library/aa559208\(v=bts.80\)).

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)  
[BlockDefault (Node Property of All Schemas)](blockdefault-node-property-of-all-schemas.md)

