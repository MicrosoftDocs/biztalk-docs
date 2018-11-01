---
title: Schema Type (Node Property of All Schemas)
TOCTitle: Schema Type (Node Property of All Schemas)
ms:assetid: b56b7f04-2e28-40c0-8f47-60902b3a9173
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578227(v=BTS.80)
ms:contentKeyID: 51530661
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Schema Type (Node Property of All Schemas)

 

Use the **Schema Type** property to specify the type of the schema being edited as either a document schema or a property schema.

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
<td><strong>Document</strong></td>
<td>Sets the <strong>schema_type</strong> attribute of the <strong>schemaInfo</strong> annotation to &quot;document&quot;, specifying that the selected schema represents an instance message.</td>
</tr>
<tr class="even">
<td><strong>Property</strong></td>
<td>Sets the <strong>schema_type</strong> attribute of the <strong>schemaInfo</strong> annotation to &quot;property&quot;, specifying that the selected schema represents one or more properties that you intend to promote. You cannot set the <strong>Schema Type</strong> property to <strong>Property</strong> unless the schema conforms to the requirements of property schemas.</td>
</tr>
<tr class="odd">
<td><strong>(Default)</strong></td>
<td>Removes the <strong>schema_type</strong> attribute, if present, which is equivalent to specifying that the selected schema represents a message (same as <strong>Document</strong>).</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, which is the same as specifying the value **Document**.

## XSD Persistence

As the value of the **schema\_type** attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor.

For detailed instructions about how to create a property schema, see [How to Create Property Schemas](https://msdn.microsoft.com/en-us/library/aa559209\(v=bts.80\)).

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

