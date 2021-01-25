---
description: "Learn more about: IBaseMessage.Context Property (COM)"
title: IBaseMessage.Context Property (COM)
TOCTitle: IBaseMessage.Context Property (COM)
ms:assetid: a7aff1ff-04bc-440e-8dcd-925d25f3d4b4
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577933(v=BTS.80)
ms:contentKeyID: 51530290
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessage.Context Property (COM)

 

Represents the message context.

## Syntax

``` c++
  
            HRESULT IBaseMessage::get_Context( // Get method  
    IBaseMessageContext**Context);   
HRESULT IBaseMessage::put_Context( // Put method:  
    IBaseMessageContext*Context);  
```

``` vb
  
Property Context
() As IBaseMessageContext  
  
```

#### Parameters

*Context*  
\[in\] When putting the property, an **IBaseMessageContext** that contains the message context. \[out, retval\] When getting the property, an **IBaseMessageContext** used to return the message context.

None.

## Return Value

These methods return an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

Not applicable.

## Error Values

These methods return an HRESULT containing one of the values in the following table.

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

The component can add properties to the context; these properties are persisted in the database if the message is submitted to the BizTalk Server Messaging Engine by using the `[SubmitMessage` method of the `IBTTransportBatch` interface.

## See Also

[IBaseMessage Interface (COM)](ibasemessage-interface-com.md)  
[IBaseMessage Members (COM)](ibasemessage-members-com.md)

