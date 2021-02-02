---
description: "Learn more about: listOfIDXRefData Document"
title: listOfIDXRefData Document
TOCTitle: listOfIDXRefData Document
ms:assetid: aa95183a-6d95-4655-89d3-f89501801c00
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577980(v=BTS.80)
ms:contentKeyID: 51530414
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# listOfIDXRefData Document

 

The **listOfIDXRefData** document contains data stored in the **xref\_IDXRefData** SQL Server table. The document has the following structure:

```C#
<?xml version="1.0" encoding="UTF-8"?>  
<listOfIDXRefData>  
    <idXRef name="Customer">  
        <appInstance name="ApplicationOne_01">  
            <appID commonID="ADDRESS6">LOCALADDRESS</appID>  
            <appID commonID="ADDRESS7">NON-LOCALADDRESS</appID>  
        </appInstance>  
    </idXRef>  
.  
.  
.  
</listOfIDXRefData>  
  
```

The document consists of one or more **idXRef** elements. The following table describes the elements of the document:

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
<td>idXRef</td>
<td></td>
<td>Contains one or more <strong>appInstance</strong> elements.</td>
</tr>
<tr class="even">
<td>idXRef</td>
<td>Name</td>
<td>A string of up to 50 characters matching one of the <strong>name</strong> elements in the <strong>listOfIDXRef</strong> document.</td>
</tr>
<tr class="odd">
<td>appInstance</td>
<td></td>
<td>Contains one or more <strong>appID</strong> elements.</td>
</tr>
<tr class="even">
<td>appInstance</td>
<td>Name</td>
<td>A string of up to 50 characters matching one of the <strong>instance</strong> elements in the <strong>listOfAppInstance</strong> document.</td>
</tr>
<tr class="odd">
<td>appID</td>
<td></td>
<td>Contains a string of up to 50 characters specific to the application and that is mapped to the corresponding <strong>commonID</strong> value.</td>
</tr>
<tr class="even">
<td>appID</td>
<td>commonID</td>
<td>A string of up to 50 characters that is mapped to the value of <strong>appID</strong>.</td>
</tr>
</tbody>
</table>


## See Also

[Importing Data for the Cross Referencing Functoids](importing-data-for-the-cross-referencing-functoids.md)  
[listOfAppInstance Document](listofappinstance-document.md)  
[listOfIDXRef Document](listofidxref-document.md)

