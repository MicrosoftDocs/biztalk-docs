---
title: INamedItem.Name Property (COM)
TOCTitle: INamedItem.Name Property (COM)
ms:assetid: 52a11191-c5e5-4288-8f06-2ef2662fb9ff
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560165(v=BTS.80)
ms:contentKeyID: 51528058
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# INamedItem.Name Property (COM)

 

Gets the name of the item.

## Syntax

``` c++
  
HRESULT INamedItem::get_Name(  
BSTR*  
Name  
);  
  
```

``` vb
  
Property Name
() As String  
  
```

#### Parameters

*Name*  
\[out,retval\] String used to return the name.

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

