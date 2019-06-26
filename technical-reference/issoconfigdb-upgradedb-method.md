---
title: ISSOConfigDB.UpgradeDB Method
TOCTitle: ISSOConfigDB.UpgradeDB Method
ms:assetid: d8be3db9-ccfc-497e-b0c8-934609534e6e
ms:mtpsurl: https://msdn.microsoft.com/library/Aa772054(v=BTS.80)
ms:contentKeyID: 51531616
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
- c++
---

# ISSOConfigDB.UpgradeDB Method

 

The UpgradeDatabase method upgrades the specified Single Sign-On (SSO) database to SSO version 3.

## Syntax

``` vb
  
Sub UpgradeDB (  
sqlServer As String,   
sqlDatabase As String  
);  
```

``` c++
  
HRESULT UpgradeDB (  
BSTR sqlServer,   
BSTR sqlDatabase  
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
<td>String containing the SQL server in which the database exists.</td>
</tr>
<tr class="even">
<td><code>sqlDatabase</code></td>
<td>String containing the name of the database.</td>
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

