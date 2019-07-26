---
title: IBaseMessage.BodyPart Property (COM)
TOCTitle: IBaseMessage.BodyPart Property (COM)
ms:assetid: e683722a-b707-4d41-8a8d-1baf742cfe1a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561640(v=BTS.80)
ms:contentKeyID: 51533029
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessage.BodyPart Property (COM)

 

Gets the body part, or main part, of the message.

## Syntax

``` c++
  
HRESULT IBaseMessage::get_BodyPart(  
IBaseMessagePart**  
BodyPart  
);  
  
```

``` vb
  
Property BodyPart
() As IBaseMessagePart  
  
```

#### Parameters

*BodyPart*  
\[out,retval\] **IBaseMessagePart** used to return the body part.

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

