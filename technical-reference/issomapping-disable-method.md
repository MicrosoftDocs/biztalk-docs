---
title: ISSOMapping.Disable Method
TOCTitle: ISSOMapping.Disable Method
ms:assetid: 261e9716-fced-40b8-a63b-f4b1b75adbeb
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa754269(v=BTS.80)
ms:contentKeyID: 51526897
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOMapping.Disable Method

 

The **Disable** method disables the mapping.

## Syntax

``` c++
  
HRESULT Disable();  
```

``` vb
  
Sub Disable
()  
```

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

