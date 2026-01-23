---
description: "Learn more about: IPipelineContext.ResourceTracker Property (COM)"
title: IPipelineContext.ResourceTracker Property (COM)
TOCTitle: IPipelineContext.ResourceTracker Property (COM)
ms:assetid: 494b8687-6238-4ae2-bd25-d9d6842a4599
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559952(v=BTS.80)
ms:contentKeyID: 51527807
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IPipelineContext.ResourceTracker Property (COM)


Reports the objects used during execution.

## Syntax

``` c++
  
HRESULT IPipelineContext::get_ResourceTracker(  
IResourceTracker*  
PipelineName  
);  
  
```

``` vb
  
Property ResourceTracker
() As IResourceTracker  
  
```

#### Parameters

*PipelineName*  
\[out,retval\] String used to return the pipeline name.

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


