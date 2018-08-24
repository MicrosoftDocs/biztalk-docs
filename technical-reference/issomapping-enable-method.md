---
title: ISSOMapping.Enable Method
TOCTitle: ISSOMapping.Enable Method
ms:assetid: 38d7a0b4-7d61-4234-9dfa-d8d13e0cbe41
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa770559(v=BTS.80)
ms:contentKeyID: 51527388
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOMapping.Enable Method

 

The **Enable** method enables the mapping.

## Syntax

``` c++
  
HRESULT Enable(  
LONG lFlags  
);  
```

``` vb
  
Sub Enable(  
lFlags As Long  
)  
```

#### Parameters

`lFlags`  
Not currently implemented.

`lFlags`  
Not currently implemented.

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

