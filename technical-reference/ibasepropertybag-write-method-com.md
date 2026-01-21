---
description: "Learn more about: IBasePropertyBag.Write Method (COM)"
title: IBasePropertyBag.Write Method (COM)
TOCTitle: IBasePropertyBag.Write Method (COM)
ms:assetid: a7a1e8bf-a3dd-49a0-bad1-9bc05f383aab
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577931(v=BTS.80)
ms:contentKeyID: 51530284
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IBasePropertyBag.Write Method (COM)

 

Adds or overwrites a property in the property bag.

## Syntax

``` c++
  
        HRESULT IBasePropertyBag::Write(  
        BSTR  
        bstrName,  
BSTRbstrNameSpace,  
VARIANTvar);  
```

``` vb
  
        Sub Write(  
        bstrName  
         As String,  
bstrNameSpace As String,  
var As Variant)  
```

#### Parameters

*bstrName*  
\[in\] String that contains the name.

*bstrName*  
**String** that contains the name.

*bstrNameSpace*  
\[in\] String that contains the name space.

*bstrNameSpace*  
**String** that contains the name space.

*var*  
\[in\] Variant that contains the context property value.

*var*  
**Variant** that contains the context property value.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

None.

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
<td>The method completed successfully.</td>
</tr>
<tr class="even">
<td>E_INVALIDARG</td>
<td>A parameter that is not valid was detected.</td>
</tr>
</tbody>
</table>


## Remarks

If vtVar is equal to VT\_NULL, the property is deleted.

## Requirements

**Platforms:**  Windows

## See Also

[IBasePropertyBag Interface (COM)](ibasepropertybag-interface-com.md)  
[IBasePropertyBag Members (COM)](ibasepropertybag-members-com.md)

