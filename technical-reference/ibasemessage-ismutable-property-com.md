---
description: "Learn more about: IBaseMessage.IsMutable Property (COM)"
title: IBaseMessage.IsMutable Property (COM)
TOCTitle: IBaseMessage.IsMutable Property (COM)
ms:assetid: 718374be-970b-4111-b950-017342f75478
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560779(v=BTS.80)
ms:contentKeyID: 51528884
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IBaseMessage.IsMutable Property (COM)

 

Gets a value that indicates whether the message context can be changed by components during processing.

## Syntax

``` c++
  
          HRESULT IBaseMessage::get_IsMutable(   
BOOLIsMutable);  
```

``` vb
  
Public ReadOnly Property IsMutable As Boolean  
  
```

#### Parameters

*IsMutable*  
\[out,retval\] **true** if the context can be changed; otherwise, **false**.

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

[IBaseMessage Interface (COM)](ibasemessage-interface-com.md)  
[IBaseMessage Members (COM)](ibasemessage-members-com.md)

