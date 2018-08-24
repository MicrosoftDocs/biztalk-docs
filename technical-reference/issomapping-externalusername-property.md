---
title: ISSOMapping.ExternalUserName Property
TOCTitle: ISSOMapping.ExternalUserName Property
ms:assetid: a09a045e-197d-4abc-a87c-ce5cb2361725
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa705079(v=BTS.80)
ms:contentKeyID: 51530077
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOMapping.ExternalUserName Property

 

The **ExternalUserName** property specifies the external (non-Microsoft Windows) user name.

## Syntax

``` c++
  
HRESULT ISSOMapping::get_ExternalUserName(BSTR* ExternalUserName);  
HRESULT ISSOMapping::put_ExternalUserName(BSTR ExternalUserName);  
  
```

``` vb
  
Property ExternalUserName
() As String  
  
```

#### Parameters

`ExternalUserName`  
\[in\] When putting the property, a string that contains the external user name. \[out, retval\] When getting the property, a string used to return the external user name.

None.

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


## Requirements

**Platforms:**  Windows

## See Also

[ISSOMapping Interface (COM)](issomapping-interface-com.md)  
[ISSOMapping Members](issomapping-members.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/en-us/library/aa704508\(v=bts.80\))

