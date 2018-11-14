---
title: ISSOLookup2.GetCredentials Method
TOCTitle: ISSOLookup2.GetCredentials Method
ms:assetid: 2e919858-90ba-4c72-98b6-cd37722aeae8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa745235(v=BTS.80)
ms:contentKeyID: 51527060
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOLookup2.GetCredentials Method

 

The **GetCredentials** method retrieves the user credentials for an application.

## Syntax

``` c++
  
HRESULT GetCredentials(  
BSTR bstrApplicationName,  
LONG lFlags,  
BSTR* pbstrExternalUserName,  
SAFEARRAY credentials  
);  
```

``` vb
  
Function GetCredentials(  
bstrApplicationName As String,  
lFlags As Long,  
pbstrExternalUserName As String  
)  
As String  
```

#### Parameters

`bstrApplicationName`  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

`bstrApplicationName`  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

`lFlags`  
\[in\] Long integer that specifies the flags to set. Using the SSO\_FLAG\_REFRESH indicates that the credential cache should be bypassed.

`lFlags`  
\[in\] Long that specifies the flags to set. Using the SSO\_FLAG\_REFRESH indicates that the credential cache should be bypassed.

`pbstrExternalUserName`  
\[out\] Pointer to a string that receives the external user name.

`pbstrExternalUserName`  
\[out\] String that receives the external user name.

`credentials`  
\[out\] String array that receives the credentials.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.

String array that receives the credentials.

## Error Values

This method returns an HRESULT containing one of the values in the following table.

This method indicates errors by setting the Number property of the global Err object to one of the values in the following table.

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

To access this method, you must be an Application User. You can only retrieve your own credential.

## Requirements

**Platforms:**  Windows

## See Also

[ISSOLookup2 Interface (COM)](issolookup2-interface-com.md)  
[ISSOLookup2 Members](issolookup2-members.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

