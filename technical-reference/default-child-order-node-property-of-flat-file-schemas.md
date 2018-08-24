---
title: Default Child Order (Node Property of Flat File Schemas)
TOCTitle: Default Child Order (Node Property of Flat File Schemas)
ms:assetid: 41c67f27-3511-4a63-ae68-7aa3589bea97
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559793(v=BTS.80)
ms:contentKeyID: 51527612
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Default Child Order (Node Property of Flat File Schemas)

 

Use the **Default Child Order** property to configure, for the entire schema, the default relationship between delimiters and the data they delimit.

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

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
<td>Use this value when the delimiter appears before the data that it is delimiting.</td>
</tr>
<tr class="even">
<td><strong>Postfix</strong></td>
<td>Use this value when the delimiter appears after the data that it is delimiting.</td>
</tr>
<tr class="odd">
<td><strong>Infix</strong></td>
<td>Use this value when the delimiter appears between different items of data, resulting in one less delimiter than when <strong>Prefix</strong> or <strong>Postfix</strong> is chosen.</td>
</tr>
<tr class="even">
<td><strong>Conditional Default</strong></td>
<td>Removes the corresponding annotation in the XSD representation of the schema, if any, resulting in the following default behavior for all <strong>Record</strong> nodes in the schema:<br />
<br />
- If a <strong>Record</strong> node has a tag identifier, then the child order will be prefix.<br />
- Otherwise, the child order will be infix.</td>
</tr>
</tbody>
</table>


## Default Value

**Conditional Default**

## XSD Persistence

As the value of the **default\_child\_order** (="prefix", "postfix", or "infix") attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.

You can override the global setting established by this property by setting the [Child Order](child-order-node-property-of-flat-file-schemas.md) property for individual **Record** nodes.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)  
[Child Order (Node Property of Flat File Schemas)](child-order-node-property-of-flat-file-schemas.md)

