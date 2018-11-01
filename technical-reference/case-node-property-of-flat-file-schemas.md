---
title: Case (Node Property of Flat File Schemas)
TOCTitle: Case (Node Property of Flat File Schemas)
ms:assetid: ea52fb87-d08d-4265-984b-d71123f51724
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561721(v=BTS.80)
ms:contentKeyID: 51533141
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Case (Node Property of Flat File Schemas)

 

Use the **Case** property to specify whether data in instance messages should be converted to all uppercase, converted to all lowercase, or left as is.

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
<td><strong>Uppercase</strong></td>
<td>Specifies that data in instance messages should be converted to uppercase when it is processed.</td>
</tr>
<tr class="even">
<td><strong>Lowercase</strong></td>
<td>Specifies that data in instance messages should be converted to lowercase when it is processed.</td>
</tr>
<tr class="odd">
<td><strong>(Default)</strong></td>
<td>Removes the corresponding annotation in the XSD representation of the schema, if any, resulting in no case conversion being performed.</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, resulting in no annotation being added to the XSD representation of the schema, and no case conversion being performed.

## XSD Persistence

As the value of the **case** (="upper" or "lower") attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

