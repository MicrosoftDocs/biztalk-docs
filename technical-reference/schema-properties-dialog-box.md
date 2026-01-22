---
description: "Learn more about: Schema Properties Dialog Box"
title: Schema Properties Dialog Box
TOCTitle: Schema Properties Dialog Box
ms:assetid: d81bff33-aa23-48bc-b77e-67993de1ae3c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578664(v=BTS.80)
ms:contentKeyID: 51531593
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: ui-reference
f1_keywords:
- bts10.admin.schema.properties
---

# Schema Properties Dialog Box

Use the **Schema Properties** window to view detailed properties about the schemas in the project. You can also select properties for tracking and locating messages.

## General Tab

Schema properties on the **General** tab—typically properties that schemas share with items such as maps and orchestrations—are configured in Microsoft® Visual Studio. The **Description** box is an exception; you can edit it in the **Schema Properties** window.

The following table lists the UIElements in the **General** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Name</strong></td>
<td>Displays the full name of the schema.</td>
</tr>
<tr class="even">
<td><strong>Assembly</strong></td>
<td>Displays the fully qualified name (name, version, culture, public key token) of the assembly that deploys the schema.</td>
</tr>
<tr class="odd">
<td><strong>Type</strong></td>
<td>Indicates whether the schema is a document schema (a message instance) or a property schema.</td>
</tr>
<tr class="even">
<td><strong>Root name</strong></td>
<td>Displays the name of the root node of the schema.</td>
</tr>
<tr class="odd">
<td><strong>Target namespace</strong></td>
<td>Displays the path of the selected schema's target namespace.</td>
</tr>
<tr class="even">
<td><strong>Description</strong></td>
<td>Type any text that helps you distinguish this schema from others. The maximum number of characters allowed is 256.</td>
</tr>
</tbody>
</table>

## Schema View Tab

The following table lists the UIElements in the **Schema View** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Schema</strong></td>
<td>Displays the contents of an XML Schema Definition (XSD) associated with the application.</td>
</tr>
</tbody>
</table>

## Tracking Tab

The following table lists the UIElements in the **Tracking** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Always track all properties</strong></td>
<td>Select this check box to indicate that all properties should be tracked regardless of version. This check box is available only for document schemas.</td>
</tr>
<tr class="even">
<td><strong>Select all message properties</strong></td>
<td>Select this check box to add all the listed properties to the Tracking database.</td>
</tr>
<tr class="odd">
<td><strong>Properties list</strong></td>
<td>Select the check box for each property that you want to use for tracking and locating messages.</td>
</tr>
</tbody>
</table>

## See Also

[XML Schemas](https://msdn.microsoft.com/library/aa559121\(v=bts.80\))  
[Different Types of BizTalk Schemas](https://msdn.microsoft.com/library/aa578053\(v=bts.80\))  
[Property Schemas](https://msdn.microsoft.com/library/aa561059\(v=bts.80\))
