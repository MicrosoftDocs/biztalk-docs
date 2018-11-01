---
title: SetUp-Files Document
TOCTitle: SetUp-Files Document
ms:assetid: f2f11033-e85e-4293-80b2-9870bb23eafd
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561908(v=BTS.80)
ms:contentKeyID: 51533408
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# SetUp-Files Document

 

The SetUp-Files document contains information about the names and locations of the data files to import. It has the following structure:

``` 
<?xml version="1.0" encoding="UTF-8"?>  
<Setup-Files>  
    <App_Type_file>c:\ListOfAppType.xml</App_Type_file>  
    <App_Instance_file>c:\ListOfAppInstance.xml</App_Instance_file>  
    <IDXRef_file>c:\ListOfIDXRef.xml</IDXRef_file>  
    <IDXRef_Data_file>c:\ListOfIDXRefData.xml</IDXRef_Data_file>  
    <ValueXRef_file>c:\ListOfValueXRef.xml</ValueXRef_file>  
    <ValueXRef_Data_file>c:\ListOfValueXRef_Data.xml</ValueXRef_Data_file>  
    <Msg_Def_file>c:\ListOfMessageDefinition.xml</Msg_Def_file>  
    <Msg_Text_file>c:\ListOfMessageText.xml</Msg_Text_file>  
</Setup-Files>  
  
```

The following table describes each element and its contents:

<table>
<thead>
<tr class="header">
<th>Element</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>App_Type_file</td>
<td>Path and name of the file containing the <strong>listOfAppType</strong> document. For more information, see <a href="listofapptype-document.md">listOfAppType Document</a> document.</td>
</tr>
<tr class="even">
<td>App_Instance_file</td>
<td>Path and name of the file containing the <strong>listOfAppInstance</strong> document. For more information, see <a href="listofappinstance-document.md">listOfAppInstance Document</a> document.</td>
</tr>
<tr class="odd">
<td>IDXRef_file</td>
<td>Path and name of the file containing the <strong>listOfIDXRef</strong> document. For more information, see <a href="listofidxref-document.md">listOfIDXRef Document</a> document.</td>
</tr>
<tr class="even">
<td>IDXRef_Data_file</td>
<td>Path and name of the file containing the <strong>listOfIDXRefData</strong> document. For more information, see <a href="listofidxrefdata-document.md">listOfIDXRefData Document</a> document.</td>
</tr>
<tr class="odd">
<td>ValueXRef_file</td>
<td>Path and name of the file containing the <strong>listOfValueXRef</strong> document. For more information, see <a href="listofvaluexref-document.md">listOfValueXRef Document</a> document.</td>
</tr>
<tr class="even">
<td>ValueXRef_Data_file</td>
<td>Path and name of the file containing the <strong>listOfValueXRefData</strong> document. For more information, see <a href="listofvaluexrefdata-document.md">listOfValueXRefData Document</a> document.</td>
</tr>
<tr class="odd">
<td>Msg_Def_file</td>
<td>Path and name of the file containing the <strong>listOfMessageDef</strong> document. For more information, see <a href="listofmessagedef-document.md">listOfMessageDef Document</a> document.</td>
</tr>
<tr class="even">
<td>Msg_Text_file</td>
<td>Path and name of the file containing the <strong>listOfMessageText</strong> document. For more information, see <a href="listofmessagetext-document.md">listOfMessageText Document</a> document.</td>
</tr>
</tbody>
</table>


You may give the files any names you choose. However, each of the files must contain the XML document of the indicated type.

## See Also

[Importing Data for the Cross Referencing Functoids](importing-data-for-the-cross-referencing-functoids.md)

