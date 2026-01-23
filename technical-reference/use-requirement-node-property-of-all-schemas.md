---
description: "Learn more about: Use Requirement (Node Property of All Schemas)"
title: Use Requirement (Node Property of All Schemas)
TOCTitle: Use Requirement (Node Property of All Schemas)
ms:assetid: 4719dab3-a493-4bef-a0e3-1f78de51de95
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559900(v=BTS.80)
ms:contentKeyID: 51527765
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
---

# Use Requirement (Node Property of All Schemas)

 

Use the **Use Requirement** property to specify whether the selected **Field Attribute** node is required in an instance message.

## Applies to Nodes of Type

[Field Attribute](field-attribute-node-properties.md)

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
<td>Removes the <strong>use</strong> attribute, if present, which is equivalent to specifying that the attribute corresponding to the selected <strong>Field Attribute</strong> node is optional in instance messages (same as <strong>Optional</strong>).</td>
</tr>
<tr class="even">
<td><strong>Optional</strong></td>
<td>Sets the <strong>use</strong> attribute to &quot;optional&quot;, specifying that the attribute corresponding to the selected <strong>Field Attribute</strong> node is optional in conforming instance messages.</td>
</tr>
<tr class="odd">
<td><strong>Prohibited</strong></td>
<td>Sets the <strong>use</strong> attribute to &quot;prohibited&quot;, specifying that the attribute corresponding to the selected <strong>Field Attribute</strong> node is not allowed in conforming instance messages. <strong>Field Attribute</strong> nodes can only be prohibited within larger structures that are being reused through derivation.</td>
</tr>
<tr class="even">
<td><strong>Required</strong></td>
<td>Sets the <strong>use</strong> attribute to &quot;required&quot;, specifying that the attribute corresponding to the selected <strong>Field Attribute</strong> node is required in conforming instance messages. You cannot set values for the <strong>Default</strong> and <strong>Fixed</strong> properties when this property is set to <strong>Required</strong>.</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, which means that **use** attribute is not present, providing the default XSD behavior of the attribute corresponding to the selected **Field Attribute** node being optional in instance messages.

## XSD Persistence

As the value of the **use** attribute (="optional", "prohibited", or "required") of the **attribute** element corresponding to the selected **Field Attribute** node.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Field Attribute** node in BizTalk Editor.

This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

