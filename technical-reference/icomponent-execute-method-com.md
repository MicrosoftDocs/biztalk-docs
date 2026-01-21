---
description: "Learn more about: IComponent.Execute Method (COM)"
title: IComponent.Execute Method (COM)
TOCTitle: IComponent.Execute Method (COM)
ms:assetid: 9d9bf0db-d6e5-4f68-a78e-a8b25d3a33fc
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577585(v=BTS.80)
ms:contentKeyID: 51529977
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IComponent.Execute Method (COM)

 

Executes a pipeline component to process the input message and get the resulting message.

## Syntax

``` c++
  
        HRESULT IComponent::Execute(  
        IPipelineContext*  
        pContext,  
IBaseMessage*pInMsg,  
IBaseMessage**ppOutMsg);  
```

``` vb
  
        Function Execute(  
        pContext  
         As IPipelineContext,  
pInMsg As IBaseMessage) As IBaseMessage  
```

#### Parameters

*pContext*  
\[in\] Reference to a **IPipelineContext** object/interface that contains the current pipeline context.

*pContext*  
**IPipelineContext** object/interface that contains the current pipeline context.

*pInMsg*  
\[in\] Reference to a **IBaseMessage** object/interface that contains the message to process.

*pInMsg*  
**IBaseMessage** object/interface that contains the message to process.

*ppOutMsg*  
\[out,retval\] Pointer to hold the reference to the returned **IBaseMessage** object/interface, which will contain the resulting message.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns an **IBaseMessage** that contains the resulting message.

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

[IComponent Interface (COM)](icomponent-interface-com.md)  
[IComponent Members (COM)](icomponent-members-com.md)

