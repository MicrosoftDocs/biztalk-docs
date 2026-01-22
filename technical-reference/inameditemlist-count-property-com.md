---
description: "Learn more about: INamedItemList.Count Property (COM)"
title: INamedItemList.Count Property (COM)
TOCTitle: INamedItemList.Count Property (COM)
ms:assetid: 9f23a437-d215-438c-9d89-8d8caeea35f5
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577633(v=BTS.80)
ms:contentKeyID: 51530083
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# INamedItemList.Count Property (COM)


Gets the number of items in the list.

## Syntax

``` c++
  
HRESULT INamedItemList::get_Count(  
LONG*  
Count  
);  
  
```

``` vb
  
Property Count
() As Long  
  
```

#### Parameters

*Count*  
\[out,retval\] Integer used to return the number of items in the list.

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

**Platforms:**  Windows

## See Also

[INamedItemList Interface (COM)](inameditemlist-interface-com.md)  
[INamedItemList Members (COM)](inameditemlist-members-com.md)

