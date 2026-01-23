---
description: "Learn more about: Preserve Delimiter For Empty Data (Node Property of Flat File Schemas)"
title: Preserve Delimiter For Empty Data (Node Property of Flat File Schemas)
TOCTitle: Preserve Delimiter For Empty Data (Node Property of Flat File Schemas)
ms:assetid: 069d5a6d-1ff1-4028-889a-4e7dfc32425d
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547057(v=BTS.80)
ms:contentKeyID: 51526005
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
---

# Preserve Delimiter For Empty Data (Node Property of Flat File Schemas)

 

Use the **Preserve Delimiter For Empty Data** property to control whether empty records and/or fields within that record will still have delimiters present in instance messages.

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
<td>Specifies that both empty fields and empty records that are immediate children of the selected <strong>Record</strong> node should have their delimiters preserved.</td>
</tr>
<tr class="even">
<td><strong>No</strong></td>
<td>Specifies that neither empty fields nor empty records that are immediate children of the selected <strong>Record</strong> node should have their delimiters preserved.</td>
</tr>
</tbody>
</table>


## Default Value

**Yes**, specifying that both empty fields and empty records that are immediate children of the selected **Record** node should have their delimiters preserved.

## XSD Persistence

As the value of the **preserve\_delimiter\_for\_empty\_data** (="true" for **Yes**, or "false" for **No**) attribute of the **element/annotation/appinfo/recordInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor and you have:

  - Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node

  - Set the **Structure** property of the selected **Record** node to **Delimited**

When a field corresponding to a **Field Element** or **Field Attribute** node is entirely missing from an instance message, the corresponding delimiter will always be generated, regardless of the setting of this property, except when a Record follows a missing optional Field.


> [!NOTE]
> <P>When a Record follows a missing optional Field, delimiters will not be preserved. For more information missing flat file delimiters, see <A href="/biztalk/core/delimiter-preservation-and-suppression">Delimiter Preservation and Suppression</A>.</P>



## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)