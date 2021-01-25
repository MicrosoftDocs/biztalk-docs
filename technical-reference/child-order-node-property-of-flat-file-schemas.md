---
description: "Learn more about: Child Order (Node Property of Flat File Schemas)"
title: Child Order (Node Property of Flat File Schemas)
TOCTitle: Child Order (Node Property of Flat File Schemas)
ms:assetid: 6de9f681-9087-48fa-985c-e18449da0820
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560706(v=BTS.80)
ms:contentKeyID: 51528770
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Child Order (Node Property of Flat File Schemas)

 

Use the **Child Order** property to configure the relationship between delimiters and the data they delimit.

## Applies to Nodes of Type

[Record](record-node-properties.md)

## Category

Flat File

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
<td><strong>Prefix</strong></td>
<td>Specifies that the delimiter appears before the data that it is delimiting.</td>
</tr>
<tr class="even">
<td><strong>Postfix</strong></td>
<td>Specifies that the delimiter appears after the data that it is delimiting.</td>
</tr>
<tr class="odd">
<td><strong>Infix</strong></td>
<td>Specifies that the delimiter appears between different items of data, resulting in one less delimiter than when <strong>Prefix</strong> or <strong>Postfix</strong> is chosen.</td>
</tr>
<tr class="even">
<td><strong>Default Child Order</strong></td>
<td>Sets the <strong>child_order</strong> attribute to &quot;default&quot;, specifying that the child order specified using the <a href="default-child-order-node-property-of-flat-file-schemas.md">Default Child Order</a> property should be used.</td>
</tr>
<tr class="odd">
<td><strong>Conditional Default</strong></td>
<td>Removes the corresponding annotation in the XSD representation of the schema, if any, resulting in the following behavior:<br />
<br />
- If the <strong>Record</strong> node has a tag identifier, then the child order will be prefix.<br />
- Otherwise, the child order will be infix.</td>
</tr>
</tbody>
</table>


## Default Value

**Conditional Default**

## XSD Persistence

As the value of the **child\_order** (="prefix", "postfix", "infix", or "default") attribute of the **element/annotation/appinfo/recordInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you have:

  - Selected a **Record** node (including a root **Record** node) in BizTalk Editor

  - Set the **Structure** property of the selected **Record** node to **Delimited**

  - Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)  
[Default Child Order (Node Property of Flat File Schemas)](default-child-order-node-property-of-flat-file-schemas.md)

