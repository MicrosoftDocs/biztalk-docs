---
description: "Learn more about: Configure Table Looping Functoid Dialog Box, Table Looping Grid Tab"
title: Configure Table Looping Functoid Dialog Box, Table Looping Grid Tab
TOCTitle: Configure Table Looping Functoid Dialog Box, Table Looping Grid Tab
ms:assetid: 8739d80f-87c1-4854-9a95-4a383f200eba
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561211(v=BTS.80)
ms:contentKeyID: 51529458
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.mapper.tablelooping
---

# Configure Table Looping Functoid Dialog Box, Table Looping Grid Tab

 

Use the **Configure Table Looping Grid** tab to configure a table of data and data sources in the source schema from which one or more **Table Extractor** functoids can be used to retrieve data at run-time and copy it to the output instance message as identified by a record or field in the destination schema.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Table cell drop-down lists</td>
<td>For this cell, select one of the relevant input parameters to this <strong>Table Looping</strong> functoid as the data to be associated with this cell.<br />
<br />
The items in the drop-down list for each cell are the set of input parameters defined for this <strong>Table Looping</strong> functoid, not including the first two input parameters, which define the dimensions of this table. The input parameters can be constant data, output from another functoid, or a location in an instance message defined by the source schema. <strong>Important:</strong> Providing descriptive labels for the input links to this <strong>Table Looping</strong> functoid are particularly useful in this scenario because the drop-down lists will show these friendly names rather than the associated XPath value.</td>
</tr>
<tr class="even">
<td><strong>Gated</strong></td>
<td>Configure whether the data in the first column is evaluated at run-time to determine whether processing the entire corresponding row will be skipped for the current iteration of the relevant record.<br />
<br />
If the first cell is output from a <strong>Logical</strong> functoid, the row is evaluated if the value is <strong>True</strong>. If the first cell is a field, then the presence of data is treated as <strong>True</strong> and the row is evaluated. The absence of data is <strong>False</strong> and the row is skipped.</td>
</tr>
</tbody>
</table>


## See Also

[Table Looping Functoid Reference](table-looping-functoid-reference.md)  
[Table Extractor Functoid Reference](table-extractor-functoid-reference.md)  
[Table Looping and Table Extractor Functoids](https://msdn.microsoft.com/library/aa559310\(v=bts.80\))  
[Table-Driven Looping Example](https://msdn.microsoft.com/library/aa578676\(v=bts.80\))

