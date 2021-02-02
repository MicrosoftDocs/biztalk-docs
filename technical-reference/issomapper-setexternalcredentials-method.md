---
description: "Learn more about: ISSOMapper.SetExternalCredentials Method"
title: ISSOMapper.SetExternalCredentials Method
TOCTitle: ISSOMapper.SetExternalCredentials Method
ms:assetid: 139abc00-7276-4148-a116-5042809b32f3
ms:mtpsurl: https://msdn.microsoft.com/library/Aa744747(v=BTS.80)
ms:contentKeyID: 51526382
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
---

# ISSOMapper.SetExternalCredentials Method

 

The **SetExternalCredentials** method stores a set of external credentials in the Enterprise Single Sign-On (SSO) server database.

## Syntax

``` c++
  
HRESULT SetExternalCredentials(  
BSTR bstrApplicationName,  
BSTR bstrExternalUserName,  
SAFEARRAY externalCredentials  
);  
```

```C#
  
[Visual Basic]  
Sub SetExternalCredentials(  
bstrApplicationName As String,  
bstrExternalUserName As String,  
externalCredentials As String  
)  
```

#### Parameters

`bstrApplicationName`  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

`bstrApplicationName`  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

`bstrExternalUserName`  
\[in\] String that specifies the external user name.

`bstrExternalUserName`  
\[in\] String that specifies the external user name.

`externalCredentials`  
\[in\] String array that specifies the external credentials to be stored.

`externalCredentials`  
\[in\] String array that specifies the external credentials to be stored.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.

Not applicable.

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

Users described as Application User can only set their own credentials. Also, the number of external credentials provided must match the number of fields expected by the external application.

## Requirements

**Platforms:**  Windows

## See Also

[ISSOMapper Interface (COM)](issomapper-interface-com.md)  
[ISSOMapper Members](issomapper-members.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

