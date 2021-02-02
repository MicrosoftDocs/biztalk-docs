---
description: "Learn more about: INamedItem.Value Property (COM)"
title: INamedItem.Value Property (COM)
TOCTitle: INamedItem.Value Property (COM)
ms:assetid: 78e8c20f-8caa-43ff-a882-f6b03edcc2a3
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560916(v=BTS.80)
ms:contentKeyID: 51529070
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# INamedItem.Value Property (COM)

 

Gets the value of the item.

## Syntax

``` c++
  
HRESULT INamedItem::get_Value(  
IUnknown**  
Value  
);  
  
```

``` vb
  
Property Value
() As IUnknown  
  
```

#### Parameters

*Value*  
\[out,retval\] **IUnknown** interface used to return the value.

None.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

Not applicable.

## Error Values

This method returns an HRESULT containing one of the values in the following table.

This property indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.

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
<td>The property was successfully obtained or written.</td>
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

[INamedItem Interface (COM)](inameditem-interface-com.md)  
[INamedItem Members (COM)](inameditem-members-com.md)

