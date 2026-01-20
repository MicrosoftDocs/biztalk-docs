---
description: "Learn more about: IAssemblerComponent.Assemble Method (COM)"
title: IAssemblerComponent.Assemble Method (COM)
TOCTitle: IAssemblerComponent.Assemble Method (COM)
ms:assetid: fe93cd74-5ddc-45b4-9427-f6380134453a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa562151(v=BTS.80)
ms:contentKeyID: 51533793
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IAssemblerComponent.Assemble Method (COM)

 

Builds an interchange from the messages that were added by the [AddDocument](iassemblercomponent-adddocument-method-com.md) method.

## Syntax

``` c++
  
        HRESULT IAssemblerComponent::Assemble(  
        IPipelineContext*  
        pContext,  
IBaseMessage**ppOutMsg);  
```

``` vb
  
Function Assemble(  
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
\[out,retval\] Pointer to hold the reference to the returned **IBaseMessage** object/interface, which will contain the assembled document.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns an **IBaseMessage** that contains the assembled document.

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

[IAssemblerComponent Methods (COM)](iassemblercomponent-methods-com.md)  
[IAssemblerComponent Interface (COM)](iassemblercomponent-interface-com.md)

