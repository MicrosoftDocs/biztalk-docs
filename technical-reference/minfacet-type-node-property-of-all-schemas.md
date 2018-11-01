---
title: MinFacet Type (Node Property of All Schemas)
TOCTitle: MinFacet Type (Node Property of All Schemas)
ms:assetid: 29a479f7-2b79-4c39-bbee-7e4293994c1b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559321(v=BTS.80)
ms:contentKeyID: 51526978
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MinFacet Type (Node Property of All Schemas)

 

Use the **MinFacet Type** property to define whether the lower bound of any instance message value corresponding to the selected **Field Element** or **Field Attribute** node, as specified by the **MinFacet Value** property, is inclusive or exclusive.

## Applies to Nodes of Type

[Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

## Category

Restricted

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
<td><strong>Exclusive</strong></td>
<td>Adds the <strong>minExclusive</strong> element as a subelement of the <strong>restriction</strong> element, specifying that the minimum value of any data associated with the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node excludes the value specified by the <strong>MinFacet Value</strong> property.</td>
</tr>
<tr class="even">
<td><strong>Inclusive</strong></td>
<td>Adds the <strong>minInclusive</strong> element as a subelement of the <strong>restriction</strong> element, specifying that the minimum value of any data associated with the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node includes the value specified by the <strong>MinFacet Value</strong> property.</td>
</tr>
<tr class="odd">
<td><strong>(Default)</strong></td>
<td>Removes any <strong>minExclusive</strong> or <strong>minInclusive</strong> element from the <strong>restriction</strong> element, specifying that there is no minimum value for any data associated with the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node. Also removes any value specified for the <strong>MinFacet Value</strong> property.</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, resulting in no **minExclusive** or **minInclusive** element within the **restriction** element and specifying that there is no minimum value for any data associated with the selected **Field Element** or **Field Attribute** node.

## XSD Persistence

As a **minExclusive** or **minInclusive** element within the **restriction** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have set its **Derived Type** property to **Restriction**. Further, you cannot set the **MinFacet Type** property until a value is entered for the **MinFacet Value** property. Then the **MinFacet Type** property defaults to **Inclusive**, but you can change it to **Exclusive**.

This property represents an XSD concept related to the **simpleType** element and its **restriction** subelement.

This property applies to ordered base data types, such as "xs:integer".

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

