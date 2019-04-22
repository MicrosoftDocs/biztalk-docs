---
title: ISSOMapping.WindowsDomainName Property
TOCTitle: ISSOMapping.WindowsDomainName Property
ms:assetid: 7f79fec5-c57a-48eb-9722-ac9988a00059
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa771356(v=BTS.80)
ms:contentKeyID: 51529244
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOMapping.WindowsDomainName Property

 

The **WindowsDomainName** property specifies the Microsoft Windows domain name.

## Syntax

``` c++
  
HRESULT ISSOMapping::get_WindowsDomainName(BSTR* WindowsDomainName);  
HRESULT ISSOMapping::put_WindowsDomainName(BSTR WindowsDomainName);  
  
```

``` vb
  
Property WindowsDomainName
() As String  
  
```

#### Parameters

`WindowsDomainName`  
\[in\] When putting the property, a string that contains the Windows domain name. Maximum length is 15 characters.

\[out, retval\] When getting the property, a string used to return the Windows domain name.

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
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

