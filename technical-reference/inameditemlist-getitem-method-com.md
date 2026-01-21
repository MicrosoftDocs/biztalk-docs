---
description: "Learn more about: INamedItemList.GetItem Method (COM)"
title: INamedItemList.GetItem Method (COM)
TOCTitle: INamedItemList.GetItem Method (COM)
ms:assetid: d61bd524-0f71-4ad9-91b1-b14a6e2f3ce2
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578638(v=BTS.80)
ms:contentKeyID: 51531660
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# INamedItemList.GetItem Method (COM)

Â 

Accesses the items in the list.

## Syntax

``` c++
  
        HRESULT INamedItemList::GetItem(  
        LONG  
        nIndex,  
INamedItem**ppRet);  
```

``` vb
  
Function GetItem(  
nIndex  
 As Long  
) As INamedItem  
  
```

#### Parameters

*nIndex*  
\[in\] Integer that contains the location in the index.

*nIndex*  
**Long** that contains the location in the index.

*ppRet*  
\[out,retval\] Pointer to hold the reference to the returned **INamedItem** object/interface, which will contain the item located at the *nindex* value.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns a **INamedItem** that contains the named item at the index location.

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

**Platforms:**Â Â Windows

## See Also

[INamedItemList Interface (COM)](inameditemlist-interface-com.md)  
[INamedItemList Members (COM)](inameditemlist-members-com.md)

