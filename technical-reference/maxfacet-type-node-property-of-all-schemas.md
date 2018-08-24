---
title: MaxFacet Type (Node Property of All Schemas)
TOCTitle: MaxFacet Type (Node Property of All Schemas)
ms:assetid: 03718aa0-e392-41fc-a389-405a2d092f73
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa546783(v=BTS.80)
ms:contentKeyID: 51525914
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MaxFacet Type (Node Property of All Schemas)

 

Use the **MaxFacet Type** property to define whether the upper bound of any instance message value corresponding to the selected **Field Element** or **Field Attribute** node, as specified by the **MaxFacet Value** property, is inclusive or exclusive.

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
<td>Adds the <strong>maxExclusive</strong> element as a subelement of the <strong>restriction</strong> element, specifying that the maximum value of any data associated with the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node excludes the value specified by the <strong>MaxFacet Value</strong> property.</td>
</tr>
<tr class="even">
<td><strong>Inclusive</strong></td>
<td>Adds the <strong>maxInclusive</strong> element as a subelement of the <strong>restriction</strong> element, specifying that the maximum value of any data associated with the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node includes the value specified by the <strong>MaxFacet Value</strong> property.</td>
</tr>
<tr class="odd">
<td><strong>(Default)</strong></td>
<td>Removes any <strong>maxExclusive</strong> or <strong>maxInclusive</strong> element from the <strong>restriction</strong> element, specifying that there is no maximum value for any data associated with the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node. Also removes any value specified for the <strong>MaxFacet Value</strong> property.</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, resulting in no **maxExclusive** or **maxInclusive** element within the **restriction** element and specifying that there is no maximum value for any data associated with the selected **Field Element** or **Field Attribute** node.

## XSD Persistence

As a **maxExclusive** or **maxInclusive** element within the **restriction** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have set its **Derived By** property to **Restriction**. Further, the **MaxFacet Type** property cannot be set until a value is entered for the **MaxFacet Value** property. Then the **MaxFacet Type** property defaults to **Inclusive**, but can be changed to **Exclusive**.

This property represents an XSD concept related to the **simpleType** element and its **restriction** subelement.

This property applies to ordered base data types, such as "xs:integer".

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

