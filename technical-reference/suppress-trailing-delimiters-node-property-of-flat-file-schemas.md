---
title: Suppress Trailing Delimiters (Node Property of Flat File Schemas)
TOCTitle: Suppress Trailing Delimiters (Node Property of Flat File Schemas)
ms:assetid: ec30cc12-a074-4077-9665-17825d7af738
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561759(v=BTS.80)
ms:contentKeyID: 51533221
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Suppress Trailing Delimiters (Node Property of Flat File Schemas)

 

Use the **Suppress Trailing Delimiter** property to suppress trailing delimiters associated with the selected **Record** node.

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
<td><strong>Yes</strong></td>
<td>Use this value to suppress trailing delimiters in instance messages.</td>
</tr>
<tr class="even">
<td><strong>No</strong></td>
<td>Use this value to include trailing delimiters in instance messages.</td>
</tr>
</tbody>
</table>


## Default Value

**No**

## XSD Persistence

As the value of the **suppress\_trailing\_delimiters** (="true" or "false") attribute of the **element/annotation/appinfo/recordInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor and you have:

  - Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node

  - Set the **Structure** property of the selected **Record** node to **Delimited**

When an element is entirely missing from an instance message, such as when it is optional, the corresponding delimiter will always be missing, regardless of the setting of this property.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

