---
title: Promote Properties Dialog Box
TOCTitle: Promote Properties Dialog Box
ms:assetid: 569f7acf-2c96-4f1e-a7a1-ccf1c893084c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560248(v=BTS.80)
ms:contentKeyID: 51528151
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.editor.props.promote
---

# Promote Properties Dialog Box

 

Use the **Promote Properties** dialog box to manage both types of property promotion: distinguished fields and property fields, where each type of promoted property is managed using its own tab on the right side of the dialog box.


> [!NOTE]
> <P>Promoted properties are restricted to non-repeating elements/attributes.</P>



<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Schema tree</strong></td>
<td>Find and select the relevant record or field that you want to promote by using either property promotion technique.</td>
</tr>
<tr class="even">
<td><strong>Distinguished Fields</strong> tab</td>
<td>Manage the distinguished field property promotions for the schema being edited.</td>
</tr>
<tr class="odd">
<td><strong>Property Fields</strong> tab</td>
<td>Manage the property schemas and property field promotions for the schema being edited.</td>
</tr>
<tr class="even">
<td><strong>Add</strong></td>
<td>Add a record or field as a promoted property, by using either the distinguished field or property field technique, depending on which tab is displayed.</td>
</tr>
<tr class="odd">
<td><strong>Remove</strong></td>
<td>Remove the selected property promotion of the type associated with the currently displayed tab; either a distinguished field promotion or a property field promotion.</td>
</tr>
<tr class="even">
<td><strong>Update</strong></td>
<td>Replace the XPath of the promoted property that is currently selected with the XPath of the node that is currently selected in the schema tree.</td>
</tr>
<tr class="odd">
<td><strong>Clear All</strong></td>
<td>Remove all property promotions of the type associated with the currently displayed tab; either all distinguished field promotions or all property field promotions.<br />
<br />
This is the same as individually removing all property promotions of the relevant type.</td>
</tr>
<tr class="even">
<td><strong>Property</strong> column of the <strong>Distinguished Fields</strong> tab</td>
<td>Display a list of the properties that have been promoted as distinguished fields.</td>
</tr>
<tr class="odd">
<td><strong>Node Path</strong> column of the <strong>Distinguished Fields</strong> tab</td>
<td>Display the XPath within the schema to the corresponding promoted property.</td>
</tr>
<tr class="even">
<td><strong>Add property schema button</strong><br />
<br />
 <img src="images/Aa560248.3d7b1a5e-7f43-4687-b01a-b2216b4b5ac2(BTS.80).jpeg" /></td>
<td>When the <strong>Property Fields</strong> tab is displayed, open the <strong>BizTalk Type Picker</strong> dialog box so that you can select a property schema to be added to the <strong>Property Schemas List</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Remove property schema button</strong><br />
<br />
 <img src="images/Aa561606.4bd6c6e7-93bf-4cdd-b1b2-8bd460a48dd9(BTS.80).jpeg" /></td>
<td>When the <strong>Property Fields</strong> tab is displayed, remove the property schema currently selected in the <strong>Property****Schemas List</strong>, if any.</td>
</tr>
<tr class="even">
<td><strong>Prefix</strong> column of <strong>Property Schemas List</strong> of the <strong>Property Fields</strong> tab</td>
<td>When the <strong>Property Fields</strong> tab is displayed, show the namespace prefix assigned to the corresponding property schema. Also, you can change the generated namespace prefix by editing it in place.</td>
</tr>
<tr class="odd">
<td><strong>Namespace</strong> column of <strong>Property Schemas List</strong> of the <strong>Property Fields</strong> tab</td>
<td>When the <strong>Property Fields</strong> tab is displayed, show the namespace URI of the corresponding property schema.</td>
</tr>
<tr class="even">
<td><strong>Location</strong> column of <strong>Property Schemas List</strong> of the <strong>Property Fields</strong> tab</td>
<td>When the <strong>Property Fields</strong> tab is displayed, show the relative file location of the corresponding property schema.</td>
</tr>
<tr class="odd">
<td><strong>Property</strong> column of <strong>Property Fields List</strong> of the <strong>Property Fields</strong> tab</td>
<td>When the <strong>Property Fields</strong> tab is displayed, provide a drop-down list from which you can select a field within one of the property schemas into which the record or field data will be promoted.</td>
</tr>
<tr class="even">
<td><strong>Node Path</strong> column of <strong>Property Fields List</strong> of the <strong>Property Fields</strong> tab</td>
<td>When the <strong>Property Fields</strong> tab is displayed, show the XPath within the schema of the record or field to be promoted into the corresponding property schema field.<br />
<br />
Use the ellipsis (<strong>...</strong>) button to the right of the cells in this column to open the <strong>Edit Instance XPath</strong> dialog box, in which you can change the record or field to be promoted by providing an alternative XPath.</td>
</tr>
</tbody>
</table>


## See Also

[Promoting Properties](https://msdn.microsoft.com/library/aa561535\(v=bts.80\))  
[Property Schemas](https://msdn.microsoft.com/library/aa561059\(v=bts.80\))

