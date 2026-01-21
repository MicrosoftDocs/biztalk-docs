---
description: "Learn more about: IBaseMessagePart.IsMutable Property (COM)"
title: IBaseMessagePart.IsMutable Property (COM)
TOCTitle: IBaseMessagePart.IsMutable Property (COM)
ms:assetid: b5b8b885-6e3a-4c31-9351-07cac7c4c4b7
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578234(v=BTS.80)
ms:contentKeyID: 51530722
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IBaseMessagePart.IsMutable Property (COM)

 

Gets a value that indicates whether the message context can be changed by components during processing.

## Syntax

``` c++
  
          HRESULT IBaseMessagePart::get_IsMutable(   
BOOLIsMutable);  
```

``` vb
  
Public ReadOnly Property IsMutable As Boolean  _  
  
```

#### Parameters

*IsMutable*  
\[out,retval\] **true** if the value can be changed; otherwise, **false**.

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

