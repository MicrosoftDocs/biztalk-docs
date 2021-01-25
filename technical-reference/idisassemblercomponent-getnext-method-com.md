---
description: "Learn more about: IDisassemblerComponent.GetNext Method (COM)"
title: IDisassemblerComponent.GetNext Method (COM)
TOCTitle: IDisassemblerComponent.GetNext Method (COM)
ms:assetid: d01f6e61-9490-4b52-9772-e16e9c5f5c0a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578511(v=BTS.80)
ms:contentKeyID: 51531370
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IDisassemblerComponent.GetNext Method (COM)

 

Gets the next message from the message set resulting from the disassembler execution.

## Syntax

``` c++
  
        HRESULT IDisassemblerComponent::GetNext(  
        IPipelineContext*  
        pContext,  
IBaseMessage**ppOutMsg);  
```

``` vb
  
Function GetNext(  
pContext  
 As IPipelineContext  
) As IBaseMessage  
  
```

#### Parameters

*pContext*  
\[in\] Reference to a **IPipelineContext** object/interface that contains the current pipeline context.

*pContext*  
**IPipelineContext** object/interface that contains the current pipeline context.

*ppOutMsg*  
\[out,retval\] Pointer to hold the reference to the returned **IBaseMessage** object/interface, which will contain the next message from the message set. Returns **NULL** if there are no more messages left.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns an [IBaseMessage](ibasemessage-interface-com.md) containing the disassembled document. Returns **NULL** if there are no more messages left.

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

**Platforms:**  Windows

## See Also

[IDisassemblerComponent Interface (COM)](idisassemblercomponent-interface-com.md)  
[IDisassemblerComponent Members (COM)](idisassemblercomponent-members-com.md)

