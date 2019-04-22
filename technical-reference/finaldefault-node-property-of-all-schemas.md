---
title: FinalDefault (Node Property of All Schemas)
TOCTitle: FinalDefault (Node Property of All Schemas)
ms:assetid: 6e5a6169-043c-4e6f-bf58-b5983f3f7650
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560720(v=BTS.80)
ms:contentKeyID: 51528802
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# FinalDefault (Node Property of All Schemas)

 

Use the **FinalDefault** property to specify a global setting that restricts different types of derivations from the data types defined for **Record**, **Field Element**, or **Field Attribute** nodes within the schema being edited.

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
<td>Removes the <strong>finalDefault</strong> attribute, if present, specifying that the default behavior should be provided.</td>
</tr>
<tr class="even">
<td><strong>All</strong></td>
<td>Sets the <strong>finalDefault</strong> attribute to &quot;#all&quot;, preventing all derivations from the data types defined for all of the <strong>Record</strong>, <strong>Field Element</strong>, and <strong>Field Attribute</strong> nodes in the schema.</td>
</tr>
<tr class="odd">
<td><strong>Restriction</strong></td>
<td>Adds &quot;restriction&quot; to the value of the <strong>finalDefault</strong> attribute, preventing derivations by restriction from the data types defined for all of the <strong>Record</strong>, <strong>Field Element</strong>, and <strong>Field Attribute</strong> nodes in the schema.</td>
</tr>
<tr class="even">
<td><strong>Extension</strong></td>
<td>Adds &quot;extension&quot; to the value of the <strong>finalDefault</strong> attribute, preventing derivations by extension from the data types defined for all of the <strong>Record</strong> nodes in the schema.</td>
</tr>
<tr class="odd">
<td><strong>List</strong></td>
<td>Adds &quot;list&quot; to the value of the <strong>finalDefault</strong> attribute, preventing derivations using lists from the data types defined for all of the <strong>Field Element</strong> and <strong>Field Attribute</strong> nodes in the schema.</td>
</tr>
<tr class="even">
<td></td>
<td></td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, specifying that there are no restrictions regarding how the data type defined for all of the **Record**, **Field Element**, and **Field Attribute** nodes in the schema can be inherited.

## XSD Persistence

As the value of the **finalDefault** attribute of the **schema** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor.

This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

The values **Restriction**, **Extension**, **List**, and **Union** can be set in combination with each other by selecting their corresponding check boxes in the **FinalDefault** property drop-down list. The corresponding values of the **finalDefault** attribute are space-separated.

You can override the global setting established by this property by setting the [Final](final-node-property-of-all-schemas.md) property for individual **Record**, **Field Element**, and **Field Attribute** nodes.

For more information about different types of derivations, see [Type Reuse and Derivations](https://msdn.microsoft.com/library/aa559208\(v=bts.80\)).

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)  
[Final (Node Property of All Schemas)](final-node-property-of-all-schemas.md)

