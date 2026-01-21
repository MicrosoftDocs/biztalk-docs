---
description: "Learn more about: ISSOConfigDB.GetDBInfo Method"
title: ISSOConfigDB.GetDBInfo Method
TOCTitle: ISSOConfigDB.GetDBInfo Method
ms:assetid: be146a0d-a29b-495a-ad54-5b546ab69b9c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa746225(v=BTS.80)
ms:contentKeyID: 51530991
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
dev_langs:
- vb
- c++
---

# ISSOConfigDB.GetDBInfo Method

 

The GetDBInfo method retrieves information about the specified database.

## Syntax

``` vb
  
Sub GetDBInfo(  
sqlServer As String,   
sqlDatabase As String,   
exists As Boolean,   
isConfigured As Boolean,   
needsUpgrade As Boolean,   
secretServer As String,   
ssoAdminAccount As String,   
ssoAffilateAdminAccount As String  
);  
```

``` c++
  
HRESULT GetDBInfo(  
string sqlServer,   
string sqlDatabase,   
out bool exists,   
out bool isConfigured,   
out bool needsUpgrade,   
out string secretServer,   
out string ssoAdminAccount,   
out string ssoAffilateAdminAccount  
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
<td><code>sqlServer</code></td>
<td>String containing the name of the SQL server.</td>
</tr>
<tr class="even">
<td><code>sqlDatabase</code></td>
<td>String containing the name of the specified database.</td>
</tr>
<tr class="odd">
<td><code>exists</code></td>
<td>Returns true if the database exists; otherwise, false.</td>
</tr>
<tr class="even">
<td><code>isConfigured</code></td>
<td>Returns true if the database is configured; otherwise, false.</td>
</tr>
<tr class="odd">
<td><code>needsUpgrade</code></td>
<td>Returns true if the database needs to be upgraded; otherwise, false.</td>
</tr>
<tr class="even">
<td><code>secretServer</code></td>
<td>Returns a string containing the name of the secret server of the database.</td>
</tr>
<tr class="odd">
<td><code>ssoAdminAccount</code></td>
<td>Returns a string containing the name of the SSO administration account.</td>
</tr>
<tr class="even">
<td><code>ssoAffilateAdminAccount</code></td>
<td>Returns a string containing the SSO affiliate administration account.</td>
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

