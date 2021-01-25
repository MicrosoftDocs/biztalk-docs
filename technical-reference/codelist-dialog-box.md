---
description: "Learn more about: CodeList Dialog Box"
title: CodeList Dialog Box
TOCTitle: CodeList Dialog Box
ms:assetid: 1531ab63-8bd6-4f12-a64e-b72757131edb
ms:mtpsurl: https://msdn.microsoft.com/library/Aa558705(v=BTS.80)
ms:contentKeyID: 51526419
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.editor.codelist
---

# CodeList Dialog Box

 

Use the **CodeList** dialog box to select which of the entries that match your choice of reference number should be added to your schema as valid enumeration values for the data in the corresponding element or attribute in instance messages described by the schema being edited.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Value</strong> column</td>
<td>Examine the possible enumeration values that correspond to the reference number set for the <strong>CodeList</strong> property of the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node.<br />
<br />
The values in this column correspond to the <strong>value</strong> column (column 2) in the corresponding table in the Microsoft Access database specified in the <strong>CodeList Database</strong> of the <strong>Schema</strong> node.</td>
</tr>
<tr class="even">
<td><strong>Value</strong> column check boxes</td>
<td>Select the check boxes for what you consider valid data for the corresponding element or attribute in instance messages described by the schema being edited.<br />
<br />
For each check box you select an <strong>enumeration</strong> element will be added to the XSD representation of the schema with its <strong>value</strong> attribute set to the value next to the check box.</td>
</tr>
<tr class="odd">
<td><strong>Description</strong> column</td>
<td>Provides a description of each corresponding value selection, which is particularly useful when the value column entries are terse, unreadable codes.<br />
<br />
The values in this column correspond to the <strong>Desc</strong> column (column 3) in the corresponding table in the Microsoft Office Access database specified in the <strong>CodeList Database</strong> of the <strong>Schema</strong> node.</td>
</tr>
</tbody>
</table>


## See Also

[CodeList (Node Property of All Schemas)](codelist-node-property-of-all-schemas.md)  
[CodeList Database (Node Property of All Schemas)](codelist-database-node-property-of-all-schemas.md)

