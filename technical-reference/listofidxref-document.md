---
title: listOfIDXRef Document
TOCTitle: listOfIDXRef Document
ms:assetid: cb319c04-aac1-4281-9585-30bcb996ece3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa548010(v=BTS.80)
ms:contentKeyID: 51531328
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# listOfIDXRef Document

 

The **listOfIDXRef** document contains data stored in the **xref\_IDXRef** SQL Server table. The document has the following structure:

``` 
<?xml version="1.0" encoding="UTF-8"?>  
<listOfIDXRef>  
    <idXRef>  
        <name>Customer</name>  
    </idXRef>  
    <idXRef>  
        <name>Order</name>  
    </idXRef>  
    <idXRef>  
        <name>Contact</name>  
    </idXRef>  
    <idXRef>  
        <name>Payment</name>  
    </idXRef>  
</listOfIDXRef>  
  
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
<td>idXRef</td>
<td>Contains a <strong>name</strong> element.</td>
</tr>
<tr class="even">
<td>Name</td>
<td>A string of up to 50 characters indicating the object type.</td>
</tr>
</tbody>
</table>


The **name** values in this document are placed in the **xref\_IDXRef** SQL Server table where they are mapped to unique integers used as values in other tables.

## See Also

[Importing Data for the Cross Referencing Functoids](importing-data-for-the-cross-referencing-functoids.md)  
[listOfIDXRefData Document](listofidxrefdata-document.md)

