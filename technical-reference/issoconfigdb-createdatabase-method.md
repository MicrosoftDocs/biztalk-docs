---
description: "Learn more about: ISSOConfigDB.CreateDatabase Method"
title: ISSOConfigDB.CreateDatabase Method
TOCTitle: ISSOConfigDB.CreateDatabase Method
ms:assetid: aaf064ed-aeae-4337-bc9c-a527f3001685
ms:mtpsurl: https://msdn.microsoft.com/library/Aa705133(v=BTS.80)
ms:contentKeyID: 51530378
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
- c++
---

# ISSOConfigDB.CreateDatabase Method

 

The CreateDatabase method creates a SQL database for SSO.

## Syntax

``` vb
  
Sub CreateDatabase(  
sqlServer As String,   
sqlDatabase As String,   
configureOnly As Boolean,   
secretServer As String,   
ssoAdminAccount As String,   
ssoAffilateAdminAccount As String  
);  
```

``` c++
  
HRESULT CreateDatabase(  
BSTR sqlServer,   
BSTR sqlDatabase,   
bool configureOnly,   
BSTR secretServer,   
BSTR ssoAdminAccount,   
BSTR ssoAffilateAdminAccount  
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
<td>String containing the name of the SQL server for the database.</td>
</tr>
<tr class="even">
<td><code>sqlDatabase</code></td>
<td>String containing the name of the SQL database.</td>
</tr>
<tr class="odd">
<td><code>configureOnly</code></td>
<td>True to configure an already-existing database; otherwise, false.</td>
</tr>
<tr class="even">
<td><code>secretServer</code></td>
<td>String containing the name of the secret server.</td>
</tr>
<tr class="odd">
<td><code>ssoAdminAccount</code></td>
<td>String containing the name of the SSO administration account for the server.</td>
</tr>
<tr class="even">
<td><code>ssoAffilateAdminAccount</code></td>
<td>String containing the name of the SSO affiliate administration account.</td>
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

