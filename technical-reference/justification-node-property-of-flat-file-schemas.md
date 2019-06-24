---
title: Justification (Node Property of Flat File Schemas)
TOCTitle: Justification (Node Property of Flat File Schemas)
ms:assetid: d26646dc-71d1-45b9-a162-82d36eeb4008
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578563(v=BTS.80)
ms:contentKeyID: 51531550
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Justification (Node Property of Flat File Schemas)

 

Use the **Justification** property to configure the justification of **Field Element** and **Field Attribute** node contents, which is used by the non-XML parsers.

## Applies to Nodes of Type

[Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

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
<td><strong>Left</strong></td>
<td>Use this value if the instance message data corresponding to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node is left-justified.</td>
</tr>
<tr class="even">
<td><strong>Right</strong></td>
<td>Use this value if the instance message data corresponding to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node is right-justified.</td>
</tr>
</tbody>
</table>


## Default Value

**Left**

## XSD Persistence

As the value of the **justification** attribute of:

  - For **Field Element** nodes, the **element/annotation/appinfo/fieldInfo** annotation element.

  - For **Field Attribute** nodes, the **attribute/annotation/appinfo/fieldInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node.

## See Also

[Supplemental Node Properties for Flat File Schemas](supplemental-node-properties-for-flat-file-schemas.md)

