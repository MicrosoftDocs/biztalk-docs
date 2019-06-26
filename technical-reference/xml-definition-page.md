---
title: XML Definition Page
TOCTitle: XML Definition Page
ms:assetid: 36e41aca-e4e1-4d8c-bf35-13498f098023
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559592(v=BTS.80)
ms:contentKeyID: 51527288
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.bre.xml
---

# XML Definition Page

 

Use the **XML Definition** page to specify a definition for an XML document element or attribute.

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
<td><strong>Document type</strong></td>
<td>Specify the fact type for the XML document. If your policy will be called by a BizTalk orchestration, use the BizTalk message fully qualified type.</td>
</tr>
<tr class="even">
<td><strong>Instance ID</strong></td>
<td>Specify the instance identifier of the XML document, so that you can distinguish it when comparing two or more facts based on the same XML element or attribute.</td>
</tr>
<tr class="odd">
<td><strong>Display name</strong></td>
<td>Specify a name for the vocabulary definition for display in rule definitions.</td>
</tr>
<tr class="even">
<td><strong>Perform &quot;Set&quot; Operation</strong></td>
<td>Specify that the definition is used as an action to assign a value to the XML element or attribute.</td>
</tr>
<tr class="odd">
<td><strong>Perform &quot;Get&quot; Operation</strong></td>
<td>Specify that the definition is used as a function to retrieve a value from the XML element or attribute.</td>
</tr>
<tr class="even">
<td><strong>Type</strong></td>
<td>Select the .NET type for the definition.</td>
</tr>
<tr class="odd">
<td><strong>XPath Selector</strong></td>
<td>Type the XPath to the XML record, element, or attribute to be selected. By default this will be the record XPath obtained from the schema.</td>
</tr>
<tr class="even">
<td><strong>XPath Field</strong></td>
<td>Type the XPath to the XML element or attribute to be selected. By default this will be the relative path from the XPath Selector obtained from the schema.</td>
</tr>
</tbody>
</table>


## See Also

[How to Create Vocabulary Definitions](https://msdn.microsoft.com/library/aa560743\(v=bts.80\))  
[Windows of the Business Rule Composer](https://msdn.microsoft.com/library/aa561030\(v=bts.80\))

