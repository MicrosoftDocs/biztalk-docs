---
title: Advanced Functoids Reference
TOCTitle: Advanced Functoids Reference
ms:assetid: 4b7a761f-510c-47ce-9506-4cb8e9ebba5c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560018(v=BTS.80)
ms:contentKeyID: 51527854
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Advanced Functoids Reference

 

Use **Advanced** functoids to create various types of data manipulation, such as implementing custom script, value mapping, and managing and extracting data from looping records.

For conceptual information about **Advanced** functoids, see [Advanced Functoids](https://msdn.microsoft.com/en-us/library/aa561121\(v=bts.80\)).

The following table shows the functoids in the **Advanced** category.

<table>
<thead>
<tr class="header">
<th>Advanced functoid</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><img src="images/Aa560747.313715e0-e73d-4806-941a-413d5ad1dee3(BTS.80).jpeg" title="Assert functoid" alt="Assert functoid" /> <a href="assert-functoid-reference.md">Assert</a></td>
<td>Enables you to test your assumptions about conditions in a map. Assertions are tested in Development builds only.</td>
</tr>
<tr class="even">
<td><img src="images/Aa547061.0f578133-d730-4d60-bc4a-2832c31294b5(BTS.80).jpeg" /> <a href="index-functoid-reference.md">Index</a></td>
<td>Provides a way to extract a particular value from a sequence of repeating values by specifying the appropriate index. Indices can also have varying degrees of scope depending on hierarchy depth and levels indicated by the index.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa560018.1c8ae190-aed0-49fc-b235-5c8b871b6b76(BTS.80).jpeg" /> <a href="iteration-functoid-reference.md">Iteration</a></td>
<td>For each repetition of a structure or value in an input instance message, outputs a monotonically increasing index.</td>
</tr>
<tr class="even">
<td><img src="images/Aa560018.1f70c94a-151c-4b07-9165-88873a0c33ff(BTS.80).jpeg" /> <a href="looping-functoid-reference.md">Looping</a></td>
<td>Used to explicitly indicate a looping relationship between a repeating structure in the source schema and a repeating structure in the destination schema.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa560018.8d9b71f3-8e19-4b2b-a393-3592b01e07f3(BTS.80).jpeg" /> <a href="mass-copy-functoid-reference.md">Mass Copy</a></td>
<td>Recursively copies all data in an input instance message, to arbitrary depth, that corresponds to a specified node in the source schema to the specified position in an output instance message.</td>
</tr>
<tr class="even">
<td><img src="images/Aa560952.061a0589-22a0-4f1b-8c75-4ba58bf042ac(BTS.80).jpeg" title="Nil Value functoid" alt="Nil Value functoid" /> <a href="nil-value-functoid-reference.md">Nil Value</a></td>
<td>Sets the value of the destination node to <strong>Nil</strong>.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa577847.8a6ab6c8-4e8b-4a53-8d3c-98303756f851(BTS.80).jpeg" /> <a href="record-count-functoid-reference.md">Record Count</a></td>
<td>Outputs the number of times a specified repeating structure or value occurs in an input instance message.</td>
</tr>
<tr class="even">
<td><img src="images/Aa560018.bd458694-6168-4c8c-90d2-da4407485122(BTS.80).jpeg" /> <a href="scripting-functoid-reference.md">Scripting</a></td>
<td>Runs custom script to create content for an output instance message or input to another functoid.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa560018.4260373f-6d17-4b60-9fc5-661d0b829824(BTS.80).jpeg" /> <a href="table-extractor-functoid-reference.md">Table Extractor</a></td>
<td>Outputs the data associated with a specified column for each row of the table looping grid of a <strong>Table Looping</strong> functoid.</td>
</tr>
<tr class="even">
<td><img src="images/Aa559129.8f4b3620-4778-4d73-a60d-b11dea1766aa(BTS.80).jpeg" /> <a href="table-looping-functoid-reference.md">Table Looping</a></td>
<td>In conjunction with one or more <strong>Table Extractor</strong> functoids, creates a repeating structure in an output instance message by using constant values, values from an instance message, and values that are output from other functoids.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa560018.7853c31e-dc26-4ffa-9608-29352508e725(BTS.80).jpeg" /> <a href="value-mapping-functoid-reference.md">Value Mapping</a></td>
<td>Allows a Boolean value to control whether an entire structure or another single value in an input instance message gets copied to an output instance message.</td>
</tr>
<tr class="even">
<td><img src="images/Aa561516.0b7c29fa-4dbc-4497-9411-86c7d1b81387(BTS.80).jpeg" /> <a href="value-mapping-flattening-functoid-reference.md">Value Mapping (Flattening)</a></td>
<td>Allows a Boolean value to control whether an entire structure in an input instance message gets copied to an output instance message, flattening the input hierarchy in the process.</td>
</tr>
</tbody>
</table>


## See Also

[Adding Advanced Functoids to a Map](https://msdn.microsoft.com/en-us/library/aa578352\(v=bts.80\))

