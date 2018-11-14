---
title: ISSOAdmin.PurgeCacheForApplication Method
TOCTitle: ISSOAdmin.PurgeCacheForApplication Method
ms:assetid: 28e49ab8-3a67-452c-8263-58903e7709e9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa745033(v=BTS.80)
ms:contentKeyID: 51526887
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOAdmin.PurgeCacheForApplication Method

 

The **PurgeCacheForApplication** method purges the cached credentials for an application on all Enterprise Single Sign-On (SSO) servers.

## Syntax

``` c++
  
HRESULT PurgeCacheForApplication(  
BSTR bstrApplicationName  
);  
```

``` vb
  
Sub PurgeCacheForApplication(  
bstrApplicationName As String  
)  
```

#### Parameters

bstrApplicationName  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

bstrApplicationName  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.

Not applicable.

## Error Values

This method returns an HRESULT containing one of the values in the following table.

This method indicates errors by setting the Number property of the global **Err** object to one of the values in the following table.

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
<td>E_INVALIDARG</td>
<td>An invalid parameter was detected.</td>
</tr>
</tbody>
</table>


## Remarks

There may be a short time delay while this operation is applied to all SSO servers.

To access this method, you must be an SSO Administrator, SSO Affiliate Administrator, or an Application Administrator.

## Requirements

**Platforms:**  Windows

## See Also

[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))  
[ISSOAdmin Interface (COM)](issoadmin-interface-com.md)  
[ISSOAdmin Members](issoadmin-members.md)

