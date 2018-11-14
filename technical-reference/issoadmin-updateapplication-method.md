---
title: ISSOAdmin.UpdateApplication Method
TOCTitle: ISSOAdmin.UpdateApplication Method
ms:assetid: 1b0f25f5-4e39-4ca4-a151-c8e01c474f45
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa704506(v=BTS.80)
ms:contentKeyID: 51526581
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOAdmin.UpdateApplication Method

 

The **UpdateApplication** method updates the application information in the Enterprise Single Sign-On (SSO) server database.

## Syntax

``` c++
  
HRESULT UpdateApplication(  
BSTR bstrApplicationName,  
BSTR bstrDescription,  
BSTR bstrContactInfo,  
BSTR bstrUserGroupName,  
BSTR bstrAdminGroupName,  
LONG lFlags,  
LONG lFlagMask  
);  
```

``` vb
  
Function UpdateApplication(  
bstrApplicationName As String,  
bstrDescription As String,  
bstrContactInfo As String,  
bstrUserGroupName As String,  
bstrAdminGroupName As String,  
lFlags As Long  
)  
```

#### Parameters

bstrApplicationName  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

bstrApplicationName  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

bstrDescription  
\[in\] String that specifies the description of the application.

bstrDescription  
\[in\] String that specifies the description of the application.

bstrContactInfo  
\[in\] String that specifies the contact information for this application.

bstrContactInfo  
\[in\] String that specifies the contact information for this application.

bstrUserGroupName  
\[in\] String that specifies the Application Users group name. This must be a valid global group.

bstrUserGroupName  
\[in\] String that specifies the Application Users group name. This must be a valid global group.

bstrAdminGroupName  
\[in\] String that specifies the Application Administrator group name. This must be a valid global group. If running as an Application Administrator, this parameter will be ignored.

bstrAdminGroupName  
\[in\] String that specifies the Application Administrator group name. This must be a valid global group. If running as an Application Administrator, this parameter will be ignored.

lFlags  
\[in\] Integer that specifies whether the application is enabled. To enable the application, set the SSO\_FLAG\_ENABLED flag.

lFlags  
\[in\] Integer that specifies whether the application is enabled. To enable the application, set the SSO\_FLAG\_ENABLED flag.

lFlagMask  
\[in\] To change the flag value, set this mask to the flag that you need to change. For example, to enable or disable Enterprise SSO, set this flag to SSO\_FLAG\_ENABLED. The *flagMask* parameter indicates which flag you want to change, while the *flags* parameter indicates the new value of that flag.

lFlagMask  
\[in\] To change the flag value, set this mask to the flag that you need to change. For example, to enable or disable Enterprise SSO, set this flag to SSO\_FLAG\_ENABLED. The *flagMask* parameter indicates which flag you want to change, while the *flags* parameter indicates the new value of that flag.

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

To access this method, you must be an SSO Administrator, SSO Affiliate Administrator, or an Application Administrator.

## Requirements

**Platforms:**  Windows

## See Also

[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))  
[ISSOAdmin Interface (COM)](issoadmin-interface-com.md)  
[enter link description here](issoadmin-members.md)

