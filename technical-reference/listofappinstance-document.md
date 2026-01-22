---
description: "Learn more about: listOfAppInstance Document"
title: listOfAppInstance Document
TOCTitle: listOfAppInstance Document
ms:assetid: 831eaa54-facf-4528-921f-3af6a5e7fd6f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561126(v=BTS.80)
ms:contentKeyID: 51529343
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# listOfAppInstance Document

 

The **listOfAppInstance** document contains data stored in the **xref\_AppInstance** SQL Server table. The document has the following structure:

```C#
<?xml version="1.0" encoding="UTF-8"?>  
<listOfAppInstance>  
    <appInstance>  
        <instance>ApplicationOne_01</instance>  
        <type>ApplicationOne</type>  
    </appInstance>  
    <appInstance>  
        <instance>ApplicationOne_02</instance>  
        <type>ApplicationOne</type>  
    </appInstance>  
    <appInstance>  
        <instance>ApplicationTwo_01</instance>  
        <type>ApplicationTwo</type>  
    </appInstance>  
    <appInstance>  
        <instance>ApplicationThree_01</instance>  
        <type>ApplicationThree</type>  
    </appInstance>  
    <appInstance>  
        <instance>ApplicationFour_01</instance>  
        <type>ApplicationFour</type>  
    </appInstance>  
</listOfAppInstance>  
  
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
<td>appInstance</td>
<td>Contains an <strong>instance</strong> element and a <strong>type</strong> element.</td>
</tr>
<tr class="even">
<td>Instance</td>
<td>A string of up to 50 characters that is an identifier for an instance of an application.</td>
</tr>
<tr class="odd">
<td>Type</td>
<td>A string of up to 50 characters indicating the application type. The value must match one of the <strong>name</strong> elements entered in the <strong>listOfAppType</strong> document.</td>
</tr>
</tbody>
</table>


The **instance** values in this document are placed in the **xref\_AppInstance** SQL Server table where they are mapped to unique integers used as values in other tables.

## See Also

[Importing Data for the Cross Referencing Functoids](importing-data-for-the-cross-referencing-functoids.md)  
[listOfAppType Document](listofapptype-document.md)

