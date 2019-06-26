---
title: Envelope (Node Property of All Schemas)
TOCTitle: Envelope (Node Property of All Schemas)
ms:assetid: b6333ccc-f8df-4078-90fe-c9b5be25f16c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578250(v=BTS.80)
ms:contentKeyID: 51530739
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Envelope (Node Property of All Schemas)

 

Use the **Envelope** property to configure whether the schema defines the structure of an envelope.

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

## Category

Reference

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
<td>Sets the <strong>is_envelope</strong> attribute to &quot;yes&quot;, specifying that the selected schema represents an envelope.</td>
</tr>
<tr class="even">
<td><strong>No</strong></td>
<td>Sets the <strong>is_envelope</strong> attribute to &quot;no&quot;, specifying that the selected schema does not represent an envelope.</td>
</tr>
<tr class="odd">
<td><strong>(Default)</strong></td>
<td>Removes the <strong>is_envelope</strong> attribute, if present, specifying that the selected schema does not represent an envelope (same as <strong>No</strong>).</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, resulting in no **is\_envelope** attribute and specifying that the selected schema does not represent an envelope.

## XSD Persistence

As the value of the **is\_envelope** (= "yes" or "no") attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor.

When you set this property to **Yes**, it means that the actual message content of the XML instance message (called the body of the message) is present somewhere inside the root **Record** node of this schema, as specified by the **Body XPath** property of that node. Therefore, you must also set additional properties based on a variety of conditions:

  - Regardless of whether an envelope schema has a single root or multiple roots, setting the **Root Reference** property is not required.

  - If an envelope schema has a single root, you must set the **Body XPath** property for that root.

  - If an envelope schema has multiple roots and the **Root Reference** property is not set, you must set the **Body XPath** property for all roots.

  - If an envelope schema has multiple roots and the **Root Reference** property is set, you must set the **Body XPath** property of the corresponding root **Record** node. You can optionally set the **Body XPath** property for the remaining roots.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

