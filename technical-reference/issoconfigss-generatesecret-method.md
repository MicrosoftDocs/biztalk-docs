---
title: ISSOConfigSS.GenerateSecret Method
TOCTitle: ISSOConfigSS.GenerateSecret Method
ms:assetid: 2d030cba-2a35-4dcc-919b-53ca0b344e50
ms:mtpsurl: https://msdn.microsoft.com/library/Aa745207(v=BTS.80)
ms:contentKeyID: 51527006
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
- c++
---

# ISSOConfigSS.GenerateSecret Method

 

The **GenerateSecret** method generates the secret for the secret server.

## Syntax

``` vb
  
GenerateSecret(  
backupFile As String,   
filePassword As String,   
filePasswordReminder As String  
);  
  
```

``` c++
  
HRESULT GenerateSecret(  
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
<td>String containing the path and name of the backup file for the secret server.</td>
</tr>
<tr class="even">
<td><code>filePassword</code></td>
<td>String containing the backup file password.</td>
</tr>
<tr class="odd">
<td><code>filePasswordReminder</code></td>
<td>String containing the secret server file password reminder</td>
</tr>
</tbody>
</table>


## Property Value/Return Value

\[C++\] This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.

\[Visual Basic\] Not Applicable.

## Exceptions

C++\] This method returns an HRESULT containing one of the values in the following table.

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

