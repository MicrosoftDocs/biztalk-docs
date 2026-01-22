---
description: "Learn more about: IBaseMessage.BodyPartName Property (COM)"
title: IBaseMessage.BodyPartName Property (COM)
TOCTitle: IBaseMessage.BodyPartName Property (COM)
ms:assetid: 2d4a3c71-8385-45f7-b214-c7108b95b67a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559394(v=BTS.80)
ms:contentKeyID: 51527014
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IBaseMessage.BodyPartName Property (COM)

 

Gets the name of the body part, or main part, of the message.

## Syntax

``` c++
  
HRESULT IBaseMessage::get_BodyPartName(  
BSTR*  
BodyPartName  
);  
  
```

``` vb
  
Property BodyPartName
() As String  
  
```

#### Parameters

*BodyPartName*  
\[out,retval\] String used to return the body part name.

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

Each message must have at most one body part. A part can be the body part of one message and a non-body part of another message.

## Requirements

**Platforms:**  Windows

## See Also

[IBaseMessage Interface (COM)](ibasemessage-interface-com.md)  
[IBaseMessage Members (COM)](ibasemessage-members-com.md)

