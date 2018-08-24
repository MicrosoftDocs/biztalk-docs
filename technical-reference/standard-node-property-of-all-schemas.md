---
title: Standard (Node Property of All Schemas)
TOCTitle: Standard (Node Property of All Schemas)
ms:assetid: 90378ade-fe27-42a2-bd25-0682ec51b65e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561372(v=BTS.80)
ms:contentKeyID: 51529674
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Standard (Node Property of All Schemas)

 

Use the **Standard** property to define the format and/or syntax of the instance messages that the schema being edited defines.

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

## Category

Reference

## Allowed Values

Any string, though it is often one of the choices from the drop-down list or one of several well-known industry standards such as "X12" or "EDIFACT".

The following table shows the drop-down list choices for the **Standard** property.

<table>
<thead>
<tr class="header">
<th>Drop-down list choice</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>XML</strong></td>
<td>Sets the <strong>standard</strong> attribute to &quot;XML&quot;, specifying that the selected schema defines the structure of XML instance messages.</td>
</tr>
<tr class="even">
<td><strong>(Default)</strong></td>
<td>Removes the <strong>standard</strong> attribute, if present, which is equivalent to specifying that the selected schema defines the structure of XML instances messages (same as <strong>XML</strong>).</td>
</tr>
<tr class="odd">
<td><strong>Flat File</strong></td>
<td>Specifies that the schema defines the structure of flat file instance messages.<br />
<br />
This choice is only available when the <strong>Flat File Extension</strong> has been enabled using the <strong>Schema Editor Extensions</strong> property. When this extension is enabled, the <strong>Standard</strong> property is automatically set to <strong>Flat File</strong>.</td>
</tr>
<tr class="even">
<td><strong>EDI</strong></td>
<td>Specifies that the schema defines the structure of EDI instance messages.<br />
<br />
This choice is only available when the <strong>EDI Schema Editor Extension</strong> has been enabled using the <strong>Schema Editor Extensions</strong> property. When this extension is enabled, the <strong>Standard</strong> property is automatically set to <strong>EDI</strong>.</td>
</tr>
</tbody>
</table>


New schema editor extensions may add new choices to this drop-down list.

## Default Value

**(Default)**, specifying that the selected schema defines the structure of XML instances messages.

## XSD Persistence

As the value of the **standard** attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Schema** node in BizTalk Editor.

If you set more than one schema editor extension, the automatic setting of this property may not be what you intend. It is a good idea to verify manually that this property is set to the proper value for your circumstances.

Use the [Standard Version](standard-version-node-property-of-all-schemas.md) property to qualify your setting of the **Standard** property with a particular version of that standard.

If you intend to use the CodeList feature, you should avoid using the period character (".") in the string you provide for this property. For additional information about this restriction, see [CodeList (Node Property of All Schemas)](codelist-node-property-of-all-schemas.md) and [CodeList Database (Node Property of All Schemas)](codelist-database-node-property-of-all-schemas.md).

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)  
[Standard Version (Node Property of All Schemas)](standard-version-node-property-of-all-schemas.md)

