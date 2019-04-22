---
title: Receipt (Node Property of All Schemas)
TOCTitle: Receipt (Node Property of All Schemas)
ms:assetid: 80f2054e-09a1-46b5-9695-b1fd6891c6e6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561073(v=BTS.80)
ms:contentKeyID: 51529276
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Receipt (Node Property of All Schemas)

 

Use the **Receipt** property to configure whether the schema represents an inbound receipt message.

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
<td>Sets the <strong>is_receipt</strong> attribute to &quot;yes&quot;, specifying that the selected schema represents an inbound receipt message. A correlator component is used to correlate an inbound receipt message with the outbound document for which it acknowledges receipt.</td>
</tr>
<tr class="even">
<td><strong>No</strong></td>
<td>Sets the <strong>is_receipt</strong> attribute to &quot;no&quot;, specifying that the selected schema does not represent an inbound receipt message.</td>
</tr>
<tr class="odd">
<td><strong>(Default)</strong></td>
<td>Removes the <strong>is_receipt</strong> attribute, if present, specifying that the selected schema does not represent an inbound receipt message (same as <strong>No</strong>).</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, specifying that the selected schema does not represent an inbound receipt message.

## XSD Persistence

As the value of the **is\_receipt** attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

