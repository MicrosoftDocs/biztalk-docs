---
description: "Learn more about: BlockDefault (Node Property of All Schemas)"
title: BlockDefault (Node Property of All Schemas)
TOCTitle: BlockDefault (Node Property of All Schemas)
ms:assetid: 86e41518-e11b-4d56-8894-c33ae8f4f9f2
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561201(v=BTS.80)
ms:contentKeyID: 51529445
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# BlockDefault (Node Property of All Schemas)

 

Use the **BlockDefault** property to prevent or restrict the types of derivations that can be used in instance messages for all data types defined by the schema being edited.

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

## Category

Advanced

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
<td>Removes the <strong>blockDefault</strong> attribute, if present, specifying that there are no restrictions on particular types of derivations that apply throughout the entire schema.</td>
</tr>
<tr class="even">
<td><strong>All</strong></td>
<td>Sets the <strong>blockDefault</strong> attribute to &quot;#all&quot;, specifying that no derivations are allowed.</td>
</tr>
<tr class="odd">
<td><strong>Restriction</strong></td>
<td>Adds &quot;restriction&quot; to the value of the <strong>blockDefault</strong> attribute, specifying that derivations by restriction are not allowed.</td>
</tr>
<tr class="even">
<td><strong>Extension</strong></td>
<td>Adds &quot;extension&quot; to the value of the <strong>blockDefault</strong> attribute, specifying that derivations by extension are not allowed.</td>
</tr>
<tr class="odd">
<td><strong>Substitution</strong></td>
<td>Adds &quot;substitution&quot; to the value of the <strong>blockDefault</strong> attribute, specifying that derivations by substitution are not allowed.</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, resulting in no global restrictions on deriving from the types in the schema being edited.

## XSD Persistence

As the value of the **blockDefault** attribute of the **schema** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor.

The values **Restriction**, **Extension**, and **Substitution** can be set in combination with each other by selecting their corresponding check boxes in the **BlockDefault** property drop-down list. The corresponding values of the **blockDefault** attribute are space-separated.

You can override the global setting established by this property by setting the [Block](block-node-property-of-all-schemas.md) property of individual **Record** nodes.

In corresponding instance messages, other derived data types can be used for a particular element unless explicitly prevented by the settings of the **Block** and/or **BlockDefault** properties, as follows:

```C#
<RecordName   
            xmlns:xsi="http://www.w3c.org/2001/XMLSchema-instance>"  
  
```

In the example above, "BaseOrDerivedTypeName" is the name of a complex type that is derived from the data type specified by the **Data Structure Type** property of the corresponding **Record** node by some allowed type of derivation (a type of derivation that is not blocked by this property or the **BlockDefault** property). For more information about different types of derivations, see [Type Reuse and Derivations](https://msdn.microsoft.com/library/aa559208\(v=bts.80\)).

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

