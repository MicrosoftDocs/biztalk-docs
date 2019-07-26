---
title: ISSOMapper.GetFieldInfo Method
TOCTitle: ISSOMapper.GetFieldInfo Method
ms:assetid: bc2a5698-f01c-44d0-b20d-6518d7b1090b
ms:mtpsurl: https://msdn.microsoft.com/library/Aa746189(v=BTS.80)
ms:contentKeyID: 51530856
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOMapper.GetFieldInfo Method

 

The **GetFieldInfo** method retrieves the field information for an application.

## Syntax

``` c++
  
HRESULT GetFieldInfo(  
BSTR bstrApplicationName,  
SAFEARRAY labels,  
SAFEARRAY flags  
);  
```

``` vb
  
Sub GetFieldInfo(  
bstrApplicationName As String,  
labels As String  
flags As Long  
)  
```

#### Parameters

`bstrApplicationName`  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

`bstrApplicationName`  
\[in\] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.

`labels`  
\[out\] String array that returns the field labels.

`labels`  
\[out\] String array that returns the field labels.

`flags`  
\[out\] Long integer array that returns the field flags.

`flags`  
\[out\] Long array that returns the field flags.

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
<td>E_FAIL</td>
<td>The application is disabled.</td>
</tr>
<tr class="even">
<td>E_INVALIDARG</td>
<td>An invalid parameter was detected.</td>
</tr>
</tbody>
</table>


## Remarks

The field information will only be returned if the application is currently enabled. An application cannot be enabled unless its field information is complete.

## Requirements

**Platforms:**  Windows

## See Also

[ISSOMapper Interface (COM)](issomapper-interface-com.md)  
[ISSOMapper Members](issomapper-members.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

