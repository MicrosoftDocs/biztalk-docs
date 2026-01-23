---
description: "Learn more about: Set Management Database Dialog Box"
title: Set Management Database Dialog Box
TOCTitle: Set Management Database Dialog Box
ms:assetid: b6efff59-1393-4ab9-8a27-592365a7edb6
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578265(v=BTS.80)
ms:contentKeyID: 51530707
ms.date: 08/30/2017
ms.topic: ui-reference
mtps_version: v=BTS.80
f1_keywords:
- bts10.tpe.database
---

# Set Management Database Dialog Box

 

Use the **Set Management Database** dialog box to specify the BizTalk Management database that contains the configuration information for the tracking profile you want to create.


> [!NOTE]
> <P>The BizTalk Management database is also referred to as the BizTalk Configuration database.</P>



<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>SQL Server</strong></td>
<td>Type the name of the computer running Microsoft SQL Server where the BizTalk Management database is located.<br />
<br />
SQL connection strings can be specified in one of two ways:<br />
<br />
- You can specify just the server name and the Tracking Profile Editor (TPE) will connect to the default port.<br />
- You can specify a server name and port pair, ServerName, and port number. The TPE will connect to the SQL server using the specified port.</td>
</tr>
<tr class="even">
<td><strong>Database name</strong></td>
<td>Select the name of the BizTalk Management database from the drop-down list.</td>
</tr>
</tbody>
</table>


## See Also

[Tracking Profile Editor](https://msdn.microsoft.com/library/aa547038\(v=bts.80\))

