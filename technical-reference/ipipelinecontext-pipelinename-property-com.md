---
description: "Learn more about: IPipelineContext.PipelineName Property (COM)"
title: IPipelineContext.PipelineName Property (COM)
TOCTitle: IPipelineContext.PipelineName Property (COM)
ms:assetid: a7906a2c-1c25-4a08-9b0a-a0900fac7e38
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577929(v=BTS.80)
ms:contentKeyID: 51530283
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IPipelineContext.PipelineName Property (COM)


Gets the name of the pipeline.

## Syntax

``` c++
  
HRESULT IPipelineContext::get_PipelineName(  
BSTR*  
PipelineName  
);  
  
```

``` vb
  
Property PipelineName
() As String  
  
```

#### Parameters

*ResourceTracker*  
\[out,retval\] IResourceTracker used to return the objects being executed.

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

**Platforms:**  Windows

## See Also

[IPipelineContext Interface (COM)](ipipelinecontext-interface-com.md)  
[IPipelineContext Members (COM)](ipipelinecontext-members-com.md)


