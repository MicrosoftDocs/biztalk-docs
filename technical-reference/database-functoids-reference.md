---
description: "Learn more about: Database Functoids Reference"
title: Database Functoids Reference
TOCTitle: Database Functoids Reference
ms:assetid: fcd72f31-d451-43fb-aa2a-23e42b0a0985
ms:mtpsurl: https://msdn.microsoft.com/library/Aa562112(v=BTS.80)
ms:contentKeyID: 51533709
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Database Functoids Reference

 

Use **Database** functoids to extract data from a database for use in an output instance message.

Database functoids fall into two categories. The first category consists of the **Database Lookup**, **Error Return**, and **Value Extractor** functoids, which are designed for general purpose retrieval of database values using Microsoft ActiveX Data Objects (ADO) recordsets. The second category consists of the **Format\*\*\*\*Message**, **Get Application ID**, **Get Application Value**, **Get Common ID**, **Get Common Value**, **Remove Application ID**, and **Set Common ID** functoids, which correspond to the methods of the **CrossReferencing** class of the **Microsoft.BizTalk.CrossReferencing** API.


> [!NOTE]
> <P>Unlike other functoids, which are written in C#, the first category of <STRONG>Database</STRONG> functoids (<STRONG>Database Lookup</STRONG>, <STRONG>Error Return</STRONG>, and <STRONG>Value Extractor</STRONG>) are not accessible from inline script that is run by using the <STRONG>Scripting</STRONG> functoid. This restriction is not true of the second category of <STRONG>Database</STRONG> functoids (that correspond to the methods of the <STRONG>CrossReferencing</STRONG> class).</P>



The **Cross Referencing** functoids—**Format Message**, **Get Application ID**, **Get Application Value**, **Get Common ID**, **Get Common Value**, **Remove Application ID**, and **Set Common ID**—look for data in specific SQL Server tables. For more information about how populate those tables and the structure of the input files, see [Importing Data for the Cross Referencing Functoids](importing-data-for-the-cross-referencing-functoids.md).

For conceptual information about **Database**functoids, see [Database Functoids](https://msdn.microsoft.com/library/aa560892\(v=bts.80\)).

The following table shows the functoids in the **Database** category.

<table>
<thead>
<tr class="header">
<th>Database functoid</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><img src="images/Aa562112.46f7eca0-1dba-456f-8720-24db8c35fae6(BTS.80).jpeg" /> <a href="database-lookup-functoid.md">Database Lookup</a></td>
<td>Retrieves a row from a database table as an ADO recordset.</td>
</tr>
<tr class="even">
<td><img src="images/Aa559365.7a3b89f4-0550-47f4-8cfa-6ff1b295005e(BTS.80).jpeg" /> <a href="error-return-functoid.md">Error Return</a></td>
<td>Captures error information, such as database connection failures, that occur during run time.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa562112.70a6fb56-e342-4bd0-87ce-7cc77984928d(BTS.80).jpeg" /> <a href="format-message-functoid.md">Format Message</a></td>
<td>Returns a formatted and localized string using argument substitution and, potentially, ID and value cross referencing.</td>
</tr>
<tr class="even">
<td><img src="images/Aa562112.96ae57bf-a9fd-4756-b802-0ccc2fbedfc3(BTS.80).jpeg" /> <a href="get-application-id-functoid.md">Get Application ID</a></td>
<td>Retrieves an identifier for an application object.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa562112.90056a7f-8635-49bd-bb2c-c0646a9aff1f(BTS.80).jpeg" /> <a href="get-application-value-functoid.md">Get Application Value</a></td>
<td>Retrieves an application value.</td>
</tr>
<tr class="even">
<td><img src="images/Aa562112.26f78937-34c9-4149-9603-519109276d7c(BTS.80).jpeg" /> <a href="get-common-id-functoid.md">Get Common ID</a></td>
<td>Retrieves an identifier for a common object.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa562112.e457cba1-6b35-4ef1-a872-19df042ea1cc(BTS.80).jpeg" /> <a href="get-common-value-functoid.md">Get Common Value</a></td>
<td>Retrieves a common value.</td>
</tr>
<tr class="even">
<td><img src="images/Aa562112.96ae57bf-a9fd-4756-b802-0ccc2fbedfc3(BTS.80).jpeg" /> <a href="remove-application-id.md">Remove Application ID</a></td>
<td>Removes the identifier for an application object.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa562112.6c2faac4-f20d-4d8c-8553-578c41c04eb9(BTS.80).jpeg" /> <a href="set-common-id-functoid.md">Set Common ID</a></td>
<td>Sets and returns an identifier for a common object.</td>
</tr>
<tr class="even">
<td><img src="images/Aa562112.8a16abc4-981d-49cb-87e5-6bb7b57b8cf0(BTS.80).jpeg" /> <a href="value-extractor-functoid.md">Value Extractor</a></td>
<td>Extracts the value from a specified column in an ADO recordset returned by the <strong>Database Lookup</strong> functoid.</td>
</tr>
</tbody>
</table>


This section also contains:

  - [Importing Data for the Cross Referencing Functoids](importing-data-for-the-cross-referencing-functoids.md)

## See Also

[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

