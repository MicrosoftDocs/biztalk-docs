---
title: ISSOConfigOM.DiscoverServer Method
TOCTitle: ISSOConfigOM.DiscoverServer Method
ms:assetid: 076f04db-1bdf-4e0a-83c2-fc224141a630
ms:mtpsurl: https://msdn.microsoft.com/library/Aa753953(v=BTS.80)
ms:contentKeyID: 51526039
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
- csharp
---

# ISSOConfigOM.DiscoverServer Method

 

The **DiscoverServers** method discovers the currently-available servers.

## Syntax

``` vb
  
Servers As String  
);  
```

``` csharp
  
BSTR Servers   
);  
```

#### Parameters

<table>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Reference</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><code>Servers</code></td>
<td>Returns a string containing the currently-available servers.</td>
</tr>
</tbody>
</table>


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

