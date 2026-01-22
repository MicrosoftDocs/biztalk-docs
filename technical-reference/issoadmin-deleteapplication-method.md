---
description: "Learn more about: ISSOAdmin.DeleteApplication Method"
title: ISSOAdmin.DeleteApplication Method
TOCTitle: ISSOAdmin.DeleteApplication Method
ms:assetid: d6accf27-285f-4059-8df4-cbed39e71f01
ms:mtpsurl: https://msdn.microsoft.com/library/Aa772027(v=BTS.80)
ms:contentKeyID: 51531556
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOAdmin.DeleteApplication Method

 

The **DeleteApplication** method deletes an application from the Enterprise Single Sign-On (SSO) server database.

## Syntax

``` c++
  
HRESULT DeleteApplication(  
BSTR bstrApplicationName  
);  
```

``` vb
  
Sub DeleteApplication(  
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
<td>S_FALSE</td>
<td>The application was not found.</td>
</tr>
<tr class="odd">
<td>E_ACCESSDENIED</td>
<td>Access is denied to the caller.</td>
</tr>
<tr class="even">
<td>E_INVALIDARG</td>
<td>An invalid parameter was detected.</td>
</tr>
</tbody>
</table>


## Remarks

All fields, mappings, and external credentials associated with this application are deleted.

To access this method, you must be an SSO Administrator or an SSO Affiliate Administrator.

## Requirements

**Platforms:**  Windows

## See Also

[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))  
[ISSOAdmin Interface (COM)](issoadmin-interface-com.md)  
[ISSOAdmin Members](issoadmin-members.md)

