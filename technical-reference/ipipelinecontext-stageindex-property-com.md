---
title: IPipelineContext.StageIndex Property (COM)
TOCTitle: IPipelineContext.StageIndex Property (COM)
ms:assetid: 7472420e-217b-4dca-a2a2-a2f78d3df186
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560831(v=BTS.80)
ms:contentKeyID: 51528949
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IPipelineContext.StageIndex Property (COM)

 

Gets the index of the pipeline stage where the current component is located.

## Syntax

``` c++
  
HRESULT IPipelineContext::get_StageIndex(  
LONG*  
StageIndex  
);  
  
```

``` vb
  
Property StageIndex
() As Long  
  
```

#### Parameters

*StageIndex*  
\[out,retval\] Integer used to return the stage index.

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

[IPipelineContext Interface (COM)](ipipelinecontext-interface-com.md)  
[IPipelineContext Members (COM)](ipipelinecontext-members-com.md)

