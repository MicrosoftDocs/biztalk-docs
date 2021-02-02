---
description: "Learn more about: BizTalk Server Cross Reference Import Tool (BTSXRefImport.exe)"
title: BizTalk Server Cross Reference Import Tool (BTSXRefImport.exe)
TOCTitle: BizTalk Server Cross Reference Import Tool (BTSXRefImport.exe)
ms:assetid: d87a26b7-753b-4605-939a-0dd99c2a50d8
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578674(v=BTS.80)
ms:contentKeyID: 51531721
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# BizTalk Server Cross Reference Import Tool (BTSXRefImport.exe)

 

The BizTalk Server Cross Reference Import tool reads data from a series of XML files and stores the information in SQL Server tables.

## Syntax

```C#
  
btsxrefimport  –file=setupfile  
```

<table>
<thead>
<tr class="header">
<th>Argument</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><em>Setupfile</em></td>
<td>An XML document file in the format described in <a href="setup-files-document.md">SetUp-Files Document</a> containing the names of the data files.</td>
</tr>
</tbody>
</table>


## Remarks

The import tool does not create the SQL Server tables. Rather, the BizTalk Server Configuration Wizard automatically creates the required tables during installation. For more information about the configuration wizard, see [Working with the Configuration Framework](https://msdn.microsoft.com/library/aa558808\(v=bts.80\)).


> [!NOTE]
> <P>On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</P>



## Example

In the following command, btsxrefimport reads the names of the data files from the XML document in the file `setupfile.xml`:

```C#
btsxrefimport –file=setupfile.xml  
```

## See Also

[SetUp-Files Document](setup-files-document.md)  
[Importing Data for the Cross Referencing Functoids](importing-data-for-the-cross-referencing-functoids.md)

