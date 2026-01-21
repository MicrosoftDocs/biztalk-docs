---
description: "Learn more about: IBaseMessage.PartCount Property (COM)"
title: IBaseMessage.PartCount Property (COM)
TOCTitle: IBaseMessage.PartCount Property (COM)
ms:assetid: 1f643699-4ff7-46ab-8c15-2bdb2421a235
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559132(v=BTS.80)
ms:contentKeyID: 51526712
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IBaseMessage.PartCount Property (COM)

 

Gets the total number of parts in the message.

## Syntax

``` c++
  
HRESULT IBaseMessage::get_PartCount(  
LONG*  
PartCount  
);  
  
```

``` vb
  
Property PartCount
() As Long  
  
```

#### Parameters

*PartCount*  
\[out, retval\] Integer used to return the number of parts in the message.

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


## Remarks

The **PartCount** property is incremented when a new part is added to the message.

## Requirements

**Platforms:**  Windows

## See Also

[IBaseMessage Interface (COM)](ibasemessage-interface-com.md)  
[IBaseMessage Members (COM)](ibasemessage-members-com.md)

