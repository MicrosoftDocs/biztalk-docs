---
title: IBaseMessage.MessageID Property (COM)
TOCTitle: IBaseMessage.MessageID Property (COM)
ms:assetid: a6fd85b4-3ad7-4884-8a80-025cdbd3630c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577917(v=BTS.80)
ms:contentKeyID: 51530323
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessage.MessageID Property (COM)

 

Gets the unique message ID for the message and binds all the message parts together.

## Syntax

``` c++
  
HRESULT IBaseMessage::get_MessageID(  
GUID*  
MessageID  
);  
  
```

``` vb
  
Property MessageID
() As GUID  
```

#### Parameters

*MessageID*  
\[out,retval\] Globally unique identifier (GUID) used to return the message ID.

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

