---
description: "Learn more about: ISSOAdmin.CreateApplication Method"
title: ISSOAdmin.CreateApplication Method
TOCTitle: ISSOAdmin.CreateApplication Method
ms:assetid: e6de84e2-658b-4521-9db8-1897fb390b8e
ms:mtpsurl: https://msdn.microsoft.com/library/Aa705499(v=BTS.80)
ms:contentKeyID: 51533042
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
dev_langs:
- c++
---

# ISSOAdmin.CreateApplication Method

 

The **CreateApplication** method creates an application in the Enterprise Single Sign-On (SSO) server database.

## Syntax

``` c++
  
HRESULT CreateApplication(  
BSTR bstrApplicationName,  
BSTR bstrDescription,  
BSTR bstrContactInfo,  
BSTR bstrUserGroupName,  
BSTR bstrAdminGroupName,  
LONG lFlags,  
LONG lNumFields  
);  
```

```C#
  
[Visual Basic]  
Sub CreateApplication(  
bstrApplicationName As String,  
bstrDescription As String,  
bstrContactInfo As String,  
bstrUserGroupName As String,  
bstrAdminGroupName As String,  
lFlags As Long,  
lNumFields As Long  
)  
```

#### Parameters

bstrApplicationName  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

bstrApplicationName  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

bstrDescription  
\[in\] String that specifies the description for the application. This parameter can be NULL, an empty string, or contain spaces.

bstrDescription  
\[in\] String that specifies the description for the application. This parameter can be NULL, an empty string, or contain spaces.

bstrContactInfo  
\[in\] String that specifies the contact information for this application. This parameter can be NULL, an empty string, or contain spaces.

bstrContactInfo  
\[in\] String that specifies the contact information for this application. This parameter can be NULL, an empty string, or contain spaces.

bstrUserGroupName  
\[in\] String that specifies the application users group name. This parameter must contain a valid global group.

bstrUserGroupName  
\[in\] String that specifies the application users group name. This parameter must contain a valid global group.

bstrAdminGroupName  
\[in\] String that specifies the Application Administrator group name. This parameter must contain a valid global group.

bstrAdminGroupName  
\[in\] String that specifies the Application Administrator group name. This parameter must contain a valid global group.

lFlags  
\[in\] Long integer that specifies whether the application is a group application. If a group application is required, specify SSO\_FLAG\_APP\_USES\_GROUP\_MAPPING.

lFlags  
\[in\] Long integer that specifies whether the application is a group application. If a group application is required, specify SSO\_FLAG\_APP\_USES\_GROUP\_MAPPING.

lNumFields  
\[in\] Long integer that specifies the number of fields that will be added for this application. The minimum value is 1 (one external user ID). An application can have no credential fields.

lNumFields  
\[in\] Long integer that specifies the number of fields that will be added for this application. The minimum value is 1 (one external user ID). An application can have no credential fields.

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

An application is always created as disabled.

After the field information is added by using the **CreateFieldInfo** method, then the application can be enabled by using the **UpdateApplication** method. The number of fields added by **CreateFieldInfo** must match the number of fields specified by the *numFields* parameter. The *numFields* value cannot be changed after the application is created.

To access this method, you must be an SSO Administrator or an SSO Affiliate Administrator.

## Requirements

**Platforms:**  Windows

## See Also

[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))  
[ISSOAdmin Interface (COM)](issoadmin-interface-com.md)  
[ISSOAdmin Members](issoadmin-members.md)

