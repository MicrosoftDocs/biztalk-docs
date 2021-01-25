---
description: "Learn more about: IDisassemblerComponent.Disassemble Method (COM)"
title: IDisassemblerComponent.Disassemble Method (COM)
TOCTitle: IDisassemblerComponent.Disassemble Method (COM)
ms:assetid: 61ad5f2a-26d8-4f47-89f3-549a267db554
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560463(v=BTS.80)
ms:contentKeyID: 51528457
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IDisassemblerComponent.Disassemble Method (COM)

 

Performs the disassembling of an incoming document.

## Syntax

``` c++
  
        HRESULT IDisassemblerComponent::Disassemble(  
        IPipelineContext*  
        pContext,  
IBaseMessage*pInMsg);  
```

``` vb
  
        Sub Disassemble(  
        pContext  
         As IPipelineContext,  
pInMsg As IBaseMessage)  
```

#### Parameters

*pContext*  
\[in\] Reference to a **IPipelineContext** object/interface that contains the current pipeline context.

*pContext*  
**IPipelineContext** object/interface that contains the current pipeline context.

*pInMsg*  
\[in\] Reference to a **IBaseMessage** object/interface that contains the message to be disassembled.

*pInMsg*  
**IBaseMessage** object/interface that contains the message to be disassembled.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

None.

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

