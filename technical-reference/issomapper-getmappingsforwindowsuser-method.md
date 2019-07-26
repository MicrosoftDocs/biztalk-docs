---
title: ISSOMapper.GetMappingsForWindowsUser Method
TOCTitle: ISSOMapper.GetMappingsForWindowsUser Method
ms:assetid: fde9d47f-7f64-4529-a687-3266fd57b8d6
ms:mtpsurl: https://msdn.microsoft.com/library/Aa705786(v=BTS.80)
ms:contentKeyID: 51533778
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOMapper.GetMappingsForWindowsUser Method

 

The **GetMappingsForWindowsUser** method retrieves the mappings for a Microsoft Windows user.

## Syntax

``` c++
  
HRESULT GetMappingsForWindowsUser(  
BSTR bstrWindowsDomainName,  
BSTR bstrWindowsUserName,  
BSTR bstrApplicationName,  
SAFEARRAY mappings  
);  
```

``` vb
  
Function GetMappingsForWindowsUser(  
bstrWindowsDomainName As String,  
bstrWindowsUserName As String,  
bstrApplicationName As String  
)  
As Variant  
```

#### Parameters

bstrWindowsDomainName  
\[in\] String that specifies the Microsoft Windows domain name. This parameter is optional, but if it is specified, the *windowsUserName* parameter must also be specified. If this parameter is not specified, the current user context is used.

bstrWindowsDomainName  
\[in\] String that specifies the Microsoft Windows domain name. This parameter is optional, but if it is specified, the *windowsUserName* parameter must also be specified. If this parameter is not specified, the current user context is used.

bstrWindowsUserName  
\[in\] String that specifies the Microsoft Windows domain name. This parameter is optional, but if it is specified, the *windowsUserName* parameter must also be specified. If this parameter is not specified, the current user context is used.

bstrWindowsUserName  
\[in\] String that specifies the Microsoft Windows domain name. This parameter is optional, but if it is specified, the *windowsUserName* parameter must also be specified. If this parameter is not specified, the current user context is used.

bstrApplicationName  
\[in\] String that specifies the external application name. If this parameter is specified, only one mapping is returned if it exists. If this parameter is NULL, all mappings for the specified user are returned. This parameter is optional.

bstrApplicationName  
\[in\] String that specifies the external application name. If this parameter is specified, only one mapping is returned if it exists. If this parameter is NULL, all mappings for the specified user are returned. This parameter is optional.

mappings  
\[out\] Object array that contains the mappings as **ISSOMapping** objects.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.

Variant array that contains the mappings as **ISSOMapping** objects.

## Error Values

This method returns an HRESULT containing one of the values in the following table.

This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.

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

An Application Administrator must specify the *bstrApplicationName* value.

Users described as Application User can only access their own mappings. They cannot access the mappings for another user.

## Requirements

**Platforms:**  Windows

## See Also

[ISSOMapper Interface (COM)](issomapper-interface-com.md)  
[ISSOMapper Members](issomapper-members.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

