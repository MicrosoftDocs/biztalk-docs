---
title: ISSOAdmin.GetApplicationInfo Method
TOCTitle: ISSOAdmin.GetApplicationInfo Method
ms:assetid: 133c0ec4-8db2-436a-8d3b-b73787a3ee91
ms:mtpsurl: https://msdn.microsoft.com/library/Aa744737(v=BTS.80)
ms:contentKeyID: 51526369
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOAdmin.GetApplicationInfo Method

 

The **GetApplicationInfo** method gets the application information from the Enterprise Single Sign-On (SSO) server database.

## Syntax

``` c++
  
HRESULT GetApplicationInfo(  
BSTR bstrApplicationName,  
BSTR* pbstrDescription,  
BSTR* pbstrContactInfo,  
BSTR* pbstrUserGroupName,  
BSTR* pbstrAdminGroupName,  
LONG* plFlags,  
LONG* plNumFields  
);  
```

``` vb
  
Function GetApplicationInfo(  
bstrApplicationName As String,  
pbstrDescription As String,  
pbstrContactInfo As String,  
pbstrUserGroupName As String,  
pbstrAdminGroupName As String,  
plFlags As Long  
)  
As Long  
```

#### Parameters

bstrApplicationName  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

bstrApplicationName  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

pbstrDescription  
\[out\] Pointer to a string that receives the description for the application.

pbstrDescription  
\[out\] String that receives the description for the application.

pbstrContactInfo  
\[out\] Pointer to a string that receives the contact information for the application.

pbstrContactInfo  
\[out\] String that receives the contact information for the application.

pbstrUserGroupName  
\[out\] Pointer to a string that receives the application user group name.

pbstrUserGroupName  
\[out\] String that receives the application user group name.

pbstrAdminGroupName  
\[out\] Pointer to a string that receives the Application Administrator group name.

pbstrAdminGroupName  
\[out\] String that receives the Application Administrator group name.

plFlags  
\[out\] Pointer to a long integer that receives the flags currently set for the application.

plFlags  
\[out\] Long that receives the flags currently set for the application.

plNumFields  
\[out\] Pointer to a long integer that receives the number of fields associated with the application.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.

This method returns a Long that receives the number of fields associated with the application.

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

To access this method, you must be an SSO Administrator, SSO Affiliate Administrator, or an SSO Application Administrator.

## Requirements

**Platforms:**  Windows

## See Also

[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))  
[ISSOAdmin Interface (COM)](issoadmin-interface-com.md)  
[ISSOAdmin Members](issoadmin-members.md)

