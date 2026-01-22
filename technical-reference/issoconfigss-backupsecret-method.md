---
description: "Learn more about: ISSOConfigSS.BackupSecret Method"
title: ISSOConfigSS.BackupSecret Method
TOCTitle: ISSOConfigSS.BackupSecret Method
ms:assetid: cf538003-412b-45e9-87d7-9d37f846533a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa771919(v=BTS.80)
ms:contentKeyID: 51531350
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
dev_langs:
- vb
- c++
---

# ISSOConfigSS.BackupSecret Method

 

The **BackupSecret** method backs up the secret server.

## Syntax

``` vb
  
backupFile As String,   
filePassword As String,   
filePasswordReminder As String  
);  
```

``` c++
  
BSTR backupFile,   
BSTR filePassword,   
BSTR filePasswordReminder  
);  
  
```

#### Parameters

<table>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><code>backupFile</code></td>
<td>String containing the path and name of the secret server backup file.</td>
</tr>
<tr class="even">
<td><code>filePassword</code></td>
<td>String containing the backup file password.</td>
</tr>
<tr class="odd">
<td><code>filePasswordReminder</code></td>
<td>String containing the secret server file password reminder.</td>
</tr>
</tbody>
</table>


## Property Value/Return Value

\[C++\] This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.

\[Visual Basic\] Not Applicable.

## Exceptions

\[C++\] This method returns an HRESULT containing one of the values in the following table.

\[Visual Basic\] This method indicates errors by setting the Number property of the global Err object to one of the values in the following table.

<table>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>S_OK</td>
<td>The method succeeded.</td>
</tr>
<tr class="even">
<td>E_ACCESSDENIED</td>
<td>Access is denied to the caller.</td>
</tr>
<tr class="odd">
<td>E_INVALIDREG</td>
<td>An invalid parameter was detected.</td>
</tr>
</tbody>
</table>

