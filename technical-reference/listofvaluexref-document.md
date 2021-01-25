---
description: "Learn more about: listOfValueXRef Document"
title: listOfValueXRef Document
TOCTitle: listOfValueXRef Document
ms:assetid: a788e25b-b9ec-4273-813c-8294bbee7cce
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577927(v=BTS.80)
ms:contentKeyID: 51530280
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# listOfValueXRef Document

 

The **listOfValueXRef** document contains data stored in the **xref\_ValueXRef** SQL Server table. The document has the following structure:

```C#
<?xml version = "1.0" encoding = "UTF-8"?>  
<listOfValueXRef>  
    <valueXRef>  
        <name>Country</name>  
    </valueXRef>  
    <valueXRef>  
        <name>Credit Term</name>  
    </valueXRef>  
    <valueXRef>  
        <name>Order Type</name>  
    </valueXRef>  
</listOfValueXRef>  
  
```

The following table describes the elements of the document:

<table>
<thead>
<tr class="header">
<th>Element</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>valueXRef</td>
<td>Contains a single <strong>name</strong> element.</td>
</tr>
<tr class="even">
<td>Name</td>
<td>A string of up to 50 characters.</td>
</tr>
</tbody>
</table>


The **name** values in this document are placed in the **xref\_ValueXRef** SQL Server table where they are mapped to unique integers used as values in other tables.

## See Also

[Importing Data for the Cross Referencing Functoids](importing-data-for-the-cross-referencing-functoids.md)  
[listOfValueXRefData Document](listofvaluexrefdata-document.md)

