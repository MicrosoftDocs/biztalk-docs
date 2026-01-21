---
description: "Learn more about: ISSOConfigSS.GetFilePasswordReminder Method"
title: ISSOConfigSS.GetFilePasswordReminder Method
TOCTitle: ISSOConfigSS.GetFilePasswordReminder Method
ms:assetid: 71833ea3-a19f-431b-b8a1-96355113d171
ms:mtpsurl: https://msdn.microsoft.com/library/Aa745427(v=BTS.80)
ms:contentKeyID: 51528880
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
dev_langs:
- vb
- csharp
---

# ISSOConfigSS.GetFilePasswordReminder Method

 

The **GetFilePasswordReminder** method gets the password reminder from the backup file.

## Syntax

``` vb
  
Function GetFilePasswordReminder(  
restoreFile as String);  
```

``` csharp
  
void GetFilePasswordReminder(  
string restoreFile,  
out string filePasswordReminder);  
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
<td>The file from which the reminder is to be retrieved.</td>
</tr>
<tr class="even">
<td><code>filePasswordReminder</code></td>
<td>The reminder for the file password.</td>
</tr>
</tbody>
</table>


## Property Value/Return Value

\[Visual Basic\] The file password reminder.

## Remarks

This function goes directly to the restore file to get the password reminder, hence the user must have read access to the restore file.

