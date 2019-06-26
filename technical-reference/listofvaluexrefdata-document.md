---
title: listOfValueXRefData Document
TOCTitle: listOfValueXRefData Document
ms:assetid: 17d7a54b-3f7b-4217-90b0-49f8f2b4e48d
ms:mtpsurl: https://msdn.microsoft.com/library/Aa558784(v=BTS.80)
ms:contentKeyID: 51526479
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# listOfValueXRefData Document

 

The **listOfValueXRefData** document contains data stored in the **xref\_ValueXRefData** SQL Server table. The document has the following structure:

```C#
<?xml version="1.0" encoding="UTF-8"?>  
<listOfValueXRefData>  
    <valueXRef name="Credit Term">  
        <appType name="ApplicationOne">  
            <appValue commonValue="Credit Term 1">001</appValue>  
            <appValue commonValue="Credit Term 2">002</appValue>  
            <appValue commonValue="Credit Term 3">003</appValue>  
            <appValue commonValue="Credit Term 4">004</appValue>  
        </appType>  
    </valueXRef>  
.  
.  
.  
</listOfValueXRefData>  
  
```

The document contains one or more **valueXRef** elements. The following table describes the parts of the document:

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
<td>valueXRef</td>
<td></td>
<td>Contains one or more <strong>appType</strong> elements.</td>
</tr>
<tr class="even">
<td>valueXRef</td>
<td>Name</td>
<td>A string of up to 50 characters that must match one of the <strong>name</strong> values in the <strong>listOfValueXRef</strong> document.</td>
</tr>
<tr class="odd">
<td>appType</td>
<td></td>
<td>Contains one or more <strong>appValue</strong> elements.</td>
</tr>
<tr class="even">
<td>appType</td>
<td>Name</td>
<td>A string of up to 50 characters that must match one of the <strong>name</strong> values in the <strong>listOfAppType</strong> document.</td>
</tr>
<tr class="odd">
<td>appValue</td>
<td></td>
<td>A string of up to 50 characters that is mapped to the value of the <strong>commonValue</strong> attribute of the element.</td>
</tr>
<tr class="even">
<td>appValue</td>
<td>commonValue</td>
<td>A string of up to 50 characters that is mapped to the value of the element.</td>
</tr>
</tbody>
</table>


## See Also

[Importing Data for the Cross Referencing Functoids](importing-data-for-the-cross-referencing-functoids.md)  
[listOfValueXRef Document](listofvaluexref-document.md)  
[listOfAppType Document](listofapptype-document.md)

