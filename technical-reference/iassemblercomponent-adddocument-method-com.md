---
title: IAssemblerComponent.AddDocument Method (COM)
TOCTitle: IAssemblerComponent.AddDocument Method (COM)
ms:assetid: f97bcd79-a576-44be-ac05-c088fa3936c7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa562039(v=BTS.80)
ms:contentKeyID: 51533545
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IAssemblerComponent.AddDocument Method (COM)

 

Adds the document to the list of messages that are included in an interchange.

## Syntax

``` c++
  
        HRESULT IAssemblerComponent::AddDocument(  
        IPipelineContext*  
        pContext,  
IBaseMessage*pInMsg);  
```

``` vb
  
        Sub AddDocument(  
        pContext  
         As IPipelineContext,  
pInMsg As IBaseMessage)  
```

#### Parameters

*pContext*  
\[in\] Reference to a [IPipelineContext](ipipelinecontext-interface-com.md) object/interface that contains the current pipeline context.

*pContext*  
[IPipelineContext](ipipelinecontext-interface-com.md) object/interface that contains the current pipeline context.

*pInMsg*  
\[in\] Reference to a [IBaseMessage](ibasemessage-interface-com.md) object/interface that contains the document to be added to the message set.

*pInMsg*  
[IBaseMessage](ibasemessage-interface-com.md) object/interface that contains the document to be added to the message set.

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

[IAssemblerComponent Interface (COM)](iassemblercomponent-interface-com.md)

