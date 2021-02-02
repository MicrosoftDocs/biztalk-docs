---
description: "Learn more about: Target Schema (Grid Property)"
title: Target Schema (Grid Property)
TOCTitle: Target Schema (Grid Property)
ms:assetid: cb07dd68-e0cb-4b69-94ba-e90d6437cda8
ms:mtpsurl: https://msdn.microsoft.com/library/Aa548007(v=BTS.80)
ms:contentKeyID: 51531214
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Target Schema (Grid Property)

 

Use the **Target Schema** property to view the chosen destination schema.

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
<td>Relative path to the destination schema file</td>
<td>Most often, the relative path is &quot;.\&quot;, indicating that the destination schema file resides in the project folder, along with the map file itself.</td>
</tr>
<tr class="even">
<td><strong>Fully Qualified Name</strong> property value</td>
<td>When the destination schema is from another BizTalk project (another assembly), the value of the <strong>Fully Qualified Name</strong> property of the destination schema is stored in this property.</td>
</tr>
<tr class="odd">
<td><strong>Inline</strong></td>
<td>Specifies that the destination schema for this map is a multipart schema from Orchestration Designer.</td>
</tr>
</tbody>
</table>


## Default Value

**Inline**

## Remarks

Normally, BizTalk Mapper stores references to the destination schema in the map file (.btm file) as a filepath (schema files) or Fully Qualified Name (schemas within assemblies). When the value of this property is set to **Inline**, the destination schema is a multipart schema from Orchestration Designer. Such schemas are thin wrappers, stored within the map file, that internally refer to the various partial schemas that make up the complete, if virtual, destination schema used to design the data mapping.


> [!NOTE]
> <P>You cannot edit the <STRONG>Target Schema</STRONG> property.</P>



## See Also

[Grid Properties](grid-properties.md)

