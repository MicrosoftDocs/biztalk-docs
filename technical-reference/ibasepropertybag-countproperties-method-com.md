---
title: IBasePropertyBag.CountProperties Method (COM)
TOCTitle: IBasePropertyBag.CountProperties Method (COM)
ms:assetid: 3701a2a2-fdc5-4e50-bb25-7c6c6fdb5c9c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559593(v=BTS.80)
ms:contentKeyID: 51527290
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBasePropertyBag.CountProperties Method (COM)

 

Gets the number of properties in the property bag.

## Syntax

``` c++
  
HRESULT IBasePropertyBag::CountProperties(  
ULONG*  
cCount  
);  
  
```

``` vb
  
Sub CountProperties(  
cCount  
 As ULONG  
)  
  
```

#### Parameters

*cCount*  
\[out\] Pointer to a **ULONG** used to return the number of properties in the property bag.

*cCount*  
ULONG used to return the number of properties in the property bag.

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


## Requirements

**Platforms:**  Windows

## See Also

[IBasePropertyBag Interface (COM)](ibasepropertybag-interface-com.md)  
[IBasePropertyBag Members (COM)](ibasepropertybag-members-com.md)

