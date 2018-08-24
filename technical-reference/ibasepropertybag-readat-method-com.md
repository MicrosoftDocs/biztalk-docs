---
title: IBasePropertyBag.ReadAt Method (COM)
TOCTitle: IBasePropertyBag.ReadAt Method (COM)
ms:assetid: 631c5fb0-1dd7-4e17-8b4e-1186c521c309
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560490(v=BTS.80)
ms:contentKeyID: 51528505
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBasePropertyBag.ReadAt Method (COM)

 

Reads the property at the specified index value in the property bag.

## Syntax

``` c++
  
        HRESULT IBasePropertyBag::ReadAt(  
        LONG  
        index,  
BSTR*pbstrName,  
BSTR*pbstrNamespace,  
VARIANT*pVar);  
```

``` vb
  
        Function ReadAt(  
        index  
         As Long,  
pbstrName As String,  
pbstrNamespace As String) As Variant  
```

#### Parameters

*index*  
\[in\] Integer that contains the index.

*index*  
**Long** that contains the index.

*pbstrName*  
\[out\] Pointer to a string used to return the property name.

*pbstrName*  
**String** used to return the property name.

*pbstrNamespace*  
\[out\] Pointer to a string used to return the property namespace.

*pbstrNamespace*  
**String** used to return the property namespace.

*pVar*  
\[out,retval\] Pointer to a Variant used to return the message context property value.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns the message context property value.

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

This method is useful for enumerating properties. Properties are indexed in the order in which they were added to the property bag.

## Requirements

**Platforms:**  Windows

## See Also

[IBasePropertyBag Interface (COM)](ibasepropertybag-interface-com.md)  
[IBasePropertyBag Members (COM)](ibasepropertybag-members-com.md)

