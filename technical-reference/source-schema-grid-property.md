---
title: Source Schema (Grid Property)
TOCTitle: Source Schema (Grid Property)
ms:assetid: 8b813b34-2322-4dbb-b906-6a300999dcde
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561284(v=BTS.80)
ms:contentKeyID: 51529561
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Source Schema (Grid Property)

 

Use the **Source Schema** property to view the chosen source schema.

## Category

General

## Allowed Values

<table>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Relative path to the source schema file</td>
<td>Most often, the relative path is &quot;.\&quot;, indicating that the source schema file resides in the project folder, along with the map file itself.</td>
</tr>
<tr class="even">
<td><strong>Fully Qualified Name</strong> property value</td>
<td>When the source schema is from another BizTalk project (another assembly), the value of the <strong>Fully Qualified Name</strong> property of the source schema is stored in this property.</td>
</tr>
<tr class="odd">
<td><strong>Inline</strong></td>
<td>Specifies that the source schema for this map is a multipart schema from Orchestration Designer.</td>
</tr>
</tbody>
</table>


## Default Value

**Inline**

## Remarks

Normally, BizTalk Mapper stores references to the source schema in the map file (.btm file) as a filepath (source schema files) or Fully Qualified Name (source schemas within assemblies). When the value of this property is set to **Inline**, the source schema is a multipart schema from Orchestration Designer. Such schemas are thin wrappers, stored within the map file, that internally refer to the various partial schemas that make up the complete, if virtual, source schema used to design the data mapping.


> [!NOTE]
> <P>You cannot edit the <STRONG>Source Schema</STRONG> property.</P>



## See Also

[Grid Properties](grid-properties.md)

