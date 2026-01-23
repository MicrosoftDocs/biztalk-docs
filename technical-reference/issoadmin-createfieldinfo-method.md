---
description: "Learn more about: ISSOAdmin.CreateFieldInfo Method"
title: ISSOAdmin.CreateFieldInfo Method
TOCTitle: ISSOAdmin.CreateFieldInfo Method
ms:assetid: cbf1cf28-bcf4-4529-ba8f-373bd9b074b9
ms:mtpsurl: https://msdn.microsoft.com/library/Aa771874(v=BTS.80)
ms:contentKeyID: 51531238
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOAdmin.CreateFieldInfo Method

 

The **CreateFieldInfo** method creates field information for an application.

## Syntax

``` c++
  
HRESULT CreateFieldInfo(  
BSTR bstrApplicationName,  
BSTR bstrLabel,  
LONG lFlags  
);  
```

``` vb
  
Sub CreateFieldInfo(  
bstrApplicationName As String,  
bstrLabel As String,  
lFlags As Long  
)  
```

#### Parameters

bstrApplicationName  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

bstrApplicationName  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

bstrLabel  
\[in\] String that specifies the label value. This parameter cannot be NULL or an empty string.

bstrLabel  
\[in\] String that specifies the label value. This parameter cannot be NULL or an empty string.

lFlags  
\[in\] Long integer specifies whether the field is masked. If a field must be masked when displayed in the user interface, specify SSO\_FLAG\_FIELD\_INFO\_MASK. The flag parameter will be ignored for the first (user ID) field, as it will not be masked.

lFlags  
\[in\] Long integer specifies whether the field is masked. If a field must be masked when displayed in the user interface, specify SSO\_FLAG\_FIELD\_INFO\_MASK. The flag parameter will be ignored for the first (user ID) field, as it will not be masked.

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

The application must exist before its field information can be created. The number of fields added must equal the *numFields* value specified when the application was created, otherwise the application will be disabled at run time.

Although the external user ID is not considered to be an external credential, it requires a field to describe how it will be displayed by the user interface. The first field created will be considered as the field that describes the external user ID. A minimum of one field is required, and typically at least two fields should be specified to provide credentials. An application can have no credentials.

To access this method, you must be an SSO Administrator, SSO Affiliate Administrator, or an SSO Application Administrator.

## Requirements

**Platforms:**  Windows

## See Also

[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))  
[ISSOAdmin Interface (COM)](issoadmin-interface-com.md)  
[ISSOAdmin Members](issoadmin-members.md)

