---
title: Database Definition Page
TOCTitle: Database Definition Page
ms:assetid: 23b8f76c-20e2-4ba8-8728-6dde4de6aa6f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559200(v=BTS.80)
ms:contentKeyID: 51526805
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.bre.database
---

# Database Definition Page

 

Use the **Database Definition** page to specify a definition for a database table or a database table column.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Definition name</strong></td>
<td>Type a definition name that is unique within the vocabulary version.</td>
</tr>
<tr class="even">
<td><strong>Definition description</strong></td>
<td>Type a description for the definition.</td>
</tr>
<tr class="odd">
<td><strong>Instance ID</strong></td>
<td>Specify the instance identifier of the database and column, so that you can distinguish two or more rows from the same table and data set in a rule definition.</td>
</tr>
<tr class="even">
<td><strong>Data type</strong></td>
<td>Select the .NET type for the definition from the drop-down list.</td>
</tr>
<tr class="odd">
<td><strong>Display name</strong></td>
<td>Specify a name for the vocabulary definition for display in rule definitions.</td>
</tr>
<tr class="even">
<td><strong>Perform &quot;Set&quot; Operation</strong></td>
<td>Specify that the definition is used as an action to assign a value to the database table column.</td>
</tr>
<tr class="odd">
<td><strong>Perform &quot;Get&quot; Operation</strong></td>
<td>Specify that the definition is used as a function to retrieve a value from the database table column.</td>
</tr>
<tr class="even">
<td><strong>Dataset</strong></td>
<td>Type the fact type of the database table. The default is the database name. Use unique names for your data sets when defining rules that compare data from distinct tables with the same schema.</td>
</tr>
<tr class="odd">
<td><strong>Binding type</strong></td>
<td>Select the database binding type from the drop-down list. Use Data connection on a single table to optimize retrieval; the engine will create a SQL query at runtime. Use Data table/data row if your binding applies to multiple queries; the application must prepopulate the table or row before it executes the policy.</td>
</tr>
</tbody>
</table>


## See Also

[How to Create Vocabulary Definitions](https://msdn.microsoft.com/library/aa560743\(v=bts.80\))  
[Windows of the Business Rule Composer](https://msdn.microsoft.com/library/aa561030\(v=bts.80\))

