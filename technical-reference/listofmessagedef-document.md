---
title: listOfMessageDef Document
TOCTitle: listOfMessageDef Document
ms:assetid: 0f2787cf-7294-4f13-9b72-fef76f91a335
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547391(v=BTS.80)
ms:contentKeyID: 51526254
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# listOfMessageDef Document

 

The **listOfMessageDef** document contains data stored in the **xref\_MessageDef** and **xref\_MessageArgument** SQL Server tables. The document has the following structure:

``` 
<?xml version="1.0" encoding="UTF-8"?>  
<listOfMessageDef>  
    <messageDef>  
        <code>INVALID_CREDIT</code>  
        <description>The credit code is not valid.</description>  
        <argumentName idXRefName="Credit Type">Credit Type</argumentName>  
    </messageDef>  
.  
.  
.  
</listOfMessageDef>  
  
```

The document contains one or more **messageDef** elements. The following table describes the parts of the document:

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
<td>messageDef</td>
<td></td>
<td>Contains <strong>code</strong>, <strong>description</strong>, and <strong>argumentName</strong> elements.</td>
</tr>
<tr class="even">
<td>code</td>
<td></td>
<td>A string of up to 50 characters that uniquely identifies the message.</td>
</tr>
<tr class="odd">
<td>description</td>
<td></td>
<td>A string of up to 1000 characters describing the message.</td>
</tr>
<tr class="even">
<td>argumentName</td>
<td></td>
<td>A string of up to 50 characters that is the name of the argument inserted in the message.</td>
</tr>
<tr class="odd">
<td>argumentName</td>
<td>idXRefName</td>
<td>A string of up to 50 characters that must match one of the <strong>idxRefName</strong> values in the <strong>listOfIDXRef</strong> document.</td>
</tr>
</tbody>
</table>


The **code** element is mapped to a unique identifier used as a value in other tables.

## See Also

[Importing Data for the Cross Referencing Functoids](importing-data-for-the-cross-referencing-functoids.md)  
[listOfIDXRef Document](listofidxref-document.md)  
[listOfMessageText Document](listofmessagetext-document.md)

