---
description: "Learn more about: Schema Node Properties in BizTalk Mapper"
title: Schema Node Properties in BizTalk Mapper
TOCTitle: Schema Node Properties in BizTalk Mapper
ms:assetid: 15cd7271-c9cb-42b1-8f2b-62fe5efdd497
ms:mtpsurl: https://msdn.microsoft.com/library/Aa558721(v=BTS.80)
ms:contentKeyID: 51526401
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Schema Node Properties in BizTalk Mapper

 

You can view but not change the values of node properties in the source and destination schemas in the Microsoft Visual Studio Properties window. If you need to change a schema node property value, you must open the schema in BizTalk Editor, change the appropriate property values, and then save the schema. You can then view the changed properties the next time you open the map that contains the schema in BizTalk Mapper.

The one exception to this rule is a schema node property that is only available for editing and viewing within BizTalk Mapper. If, in BizTalk Mapper, you select a **Record** node (with its **Mixed** property set to **True**), **Field Element** node, or **Field Attribute** node, the **Value** property can be set and subsequently examined.

The following table describes the source and destination schema node property that can be set from within BizTalk Mapper.

<table>
<thead>
<tr class="header">
<th>Property name</th>
<th>Category</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="value-schema-node-property.md">Value</a></td>
<td>General</td>
<td>Specifies a default value for the selected node for use during transformation.</td>
</tr>
</tbody>
</table>

