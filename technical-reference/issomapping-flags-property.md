---
title: ISSOMapping.Flags Property
TOCTitle: ISSOMapping.Flags Property
ms:assetid: 86169c9e-24e4-4260-9f91-4980a08134af
ms:mtpsurl: https://msdn.microsoft.com/library/Aa771476(v=BTS.80)
ms:contentKeyID: 51529423
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOMapping.Flags Property

 

The **Flags** property is reserved for internal use only.

## Syntax

``` c++
  
HRESULT ISSOMapping::get_Flags(BSTR* Flags);  
HRESULT ISSOMapping::put_Flags(BSTR Flags);  
  
```

``` vb
  
Property Flags() As String  
  
```

#### Parameters

`Flags`  
\[in\] When putting the property, a string that contains the flag value. \[out, retval\] When getting the property, a string used to return the flag value.

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

