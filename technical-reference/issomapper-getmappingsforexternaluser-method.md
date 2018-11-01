---
title: ISSOMapper.GetMappingsForExternalUser Method
TOCTitle: ISSOMapper.GetMappingsForExternalUser Method
ms:assetid: fdc06da6-1806-4b18-95bf-76a7486132d0
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa705785(v=BTS.80)
ms:contentKeyID: 51533729
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOMapper.GetMappingsForExternalUser Method

 

The **GetMappingsForExternalUser** method retrieves the mappings for an external user.

## Syntax

``` c++
  
HRESULT GetMappingsForExternalUser(  
BSTR bstrApplicationName,  
BSTR bstrExternalUserName,  
SAFEARRAY mappings  
);  
```

``` vb
  
Function GetMappingsForExternalUser(  
bstrApplicationName As String,  
bstrExternalUserName As String)  
As Variant  
  
```

#### Parameters

`bstrApplicationName`  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

`bstrApplicationName`  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

`bstrExternalUserName`  
\[in\] String that specifies the external user name. This value can contain spaces. If a NULL value is specified for this parameter, all mappings are returned for the specified application.

`bstrExternalUserName`  
\[in\] String that specifies the external user name. This value can contain spaces. If a NULL value is specified for this parameter, all mappings are returned for the specified application.

`mappings`  
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


## Requirements

**Platforms:**  Windows

## See Also

[ISSOMapper Interface (COM)](issomapper-interface-com.md)  
[ISSOMapper Members](issomapper-members.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/en-us/library/aa704508\(v=bts.80\))

