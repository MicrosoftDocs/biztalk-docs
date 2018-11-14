---
title: ISSOMapping.Delete Method
TOCTitle: ISSOMapping.Delete Method
ms:assetid: af2fb3e2-6185-4b6f-b0e2-305c8c320c5b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa705200(v=BTS.80)
ms:contentKeyID: 51530546
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOMapping.Delete Method

 

The **Delete** method deletes the mapping.

## Syntax

``` c++
  
HRESULT Delete();  
```

``` vb
  
Sub Delete
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


## Remarks

After the mapping has been deleted, the mapping object can no longer be used and should be released.

## Requirements

**Platforms:**  Windows

## See Also

[ISSOMapping Interface (COM)](issomapping-interface-com.md)  
[ISSOMapping Members](issomapping-members.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

