---
title: <Map File> Property Page Dialog Box, Test Map Tab
TOCTitle: <Map File> Property Page Dialog Box, Test Map Tab
ms:assetid: f0c35338-138e-47ad-9f41-19e017bd7d68
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561850(v=BTS.80)
ms:contentKeyID: 51533337
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.mapper.props.testmap
---

# \<Map File\> Property Page Dialog Box, Test Map Tab

 

Use the **Test Map** tab on the **\<Map File\> Property Page** dialog box to select files and file formats related to testing maps.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Validate TestMap Input</strong></td>
<td>Configure whether the input instance message being used to test the current map will be validated as conforming to its source schema prior to performing the mapping.</td>
</tr>
<tr class="even">
<td><strong>Validate TestMap Output</strong></td>
<td>Configure whether the output instance message that results from testing the current map will be validated as conforming to its destination schema after the mapping has been performed.</td>
</tr>
<tr class="odd">
<td><strong>TestMap Input Instance</strong></td>
<td>Name the input instance message used to test the map.<br />
<br />
Either type the path and name of the input instance message or use the ellipsis (<strong>...</strong>) button in this property value field to open the <strong>Select Input File</strong> dialog box, from which you can browse to the file you want.</td>
</tr>
<tr class="even">
<td><strong>TestMap Input</strong></td>
<td>Specify whether BizTalk Mapper will automatically generate an input instance message for use in testing the map, or if using an existing instance message, as specified by <strong>TestMap Input Instance</strong>, the format of that message (XML versus Native).</td>
</tr>
<tr class="odd">
<td><strong>TestMap Output</strong></td>
<td>Specify the format (XML versus Native) of the output instance message generated when testing a map.</td>
</tr>
</tbody>
</table>


## See Also

[Validating Instance Data](https://msdn.microsoft.com/library/aa559017\(v=bts.80\))  
[How to Test Maps](https://msdn.microsoft.com/library/aa560292\(v=bts.80\))  
[How to Validate Maps](https://msdn.microsoft.com/library/aa578098\(v=bts.80\))

