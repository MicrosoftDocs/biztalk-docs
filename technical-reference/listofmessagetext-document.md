---
description: "Learn more about: listOfMessageText Document"
title: listOfMessageText Document
TOCTitle: listOfMessageText Document
ms:assetid: 4cd90d1f-aa32-4844-b7f9-206e5a001336
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560046(v=BTS.80)
ms:contentKeyID: 51527888
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
---

# listOfMessageText Document

 

The **listOfMessageText** document contains data stored in the **xref\_MessageText** SQL Server table. The document has the following structure:

```C#
<?xml version="1.0" encoding="UTF-8"?>  
<listOfMessageText lang="en-us">  
    <messageText code="INVALID_CREDIT">Invalid Credit '%1'</messageText>  
.  
.  
.  
</listOfMessageText>  
  
```

The document contains one or more **messageText** elements. The following table describes the parts of the document:

<table>
<thead>
<tr class="header">
<th>Element</th>
<th>Attribute</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>messageText</td>
<td></td>
<td>A parameterized string of up to 1000 characters containing the text of a message.</td>
</tr>
<tr class="even">
<td>messageText</td>
<td>Code</td>
<td>A string of up to 50 characters that must match one of the <strong>code</strong> values in the <strong>listOfMessageDef</strong> document.</td>
</tr>
</tbody>
</table>


## See Also

[Importing Data for the Cross Referencing Functoids](importing-data-for-the-cross-referencing-functoids.md)  
[listOfMessageDef Document](listofmessagedef-document.md)

