---
title: ISSOConfigSS.RestoreSecret Method
TOCTitle: ISSOConfigSS.RestoreSecret Method
ms:assetid: 6b5dabed-0b56-4aad-9e2c-228a0c044638
ms:mtpsurl: https://msdn.microsoft.com/library/Aa745341(v=BTS.80)
ms:contentKeyID: 51528738
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
- csharp
---

# ISSOConfigSS.RestoreSecret Method

 

The **RestoreSecret** method restores master secrets from the password protected backup file.

## Syntax

``` vb
  
Sub RestoreSecret(  
restoreFile as String,  
filePassword as String);  
```

``` csharp
  
void RestoreSecret(  
string restoreFile,  
string filePassword);  
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
<td><code>restoreFile</code></td>
<td>The file from which the secrets are to be restored.</td>
</tr>
<tr class="even">
<td><code>filePasswordReminder</code></td>
<td>The password used to protect the restore file.</td>
</tr>
</tbody>
</table>

