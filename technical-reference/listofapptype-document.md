---
title: listOfAppType Document
TOCTitle: listOfAppType Document
ms:assetid: 6ac0e2e8-5656-4a0b-87c7-a0dac590fc80
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560643(v=BTS.80)
ms:contentKeyID: 51528712
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# listOfAppType Document

 

The **listOfAppType** document contains data stored in the **xref\_AppType** SQL Server table. The document has the following structure:

``` 
<?xml version="1.0" encoding="UTF-8"?>  
<listOfAppType>  
    <appType>  
        <name>ApplicationOne</name>  
    </appType>  
    <appType>  
        <name>ApplicationTwo</name>  
    </appType>  
    <appType>  
        <name>ApplicationThree</name>  
    </appType>  
    <appType>  
        <name>ApplicationFour</name>  
    </appType>  
</listOfAppType>  
  
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
<td>appType</td>
<td>Contains a single <strong>name</strong> element.</td>
</tr>
<tr class="even">
<td>Name</td>
<td>A string of up to 50 characters that is the name of an application.</td>
</tr>
</tbody>
</table>


The names in this document are placed in the **xref\_AppType** SQL Server table where they are mapped to unique integers used as values in other tables.

## See Also

[Importing Data for the Cross Referencing Functoids](importing-data-for-the-cross-referencing-functoids.md)  
[listOfAppInstance Document](listofappinstance-document.md)

