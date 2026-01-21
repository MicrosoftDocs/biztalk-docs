---
description: "Learn more about: IPipelineContext.PipelineID Property (COM)"
title: IPipelineContext.PipelineID Property (COM)
TOCTitle: IPipelineContext.PipelineID Property (COM)
ms:assetid: 64f2aeab-f362-407a-b549-206f8760d76a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560520(v=BTS.80)
ms:contentKeyID: 51528533
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IPipelineContext.PipelineID Property (COM)


Gets the ID of the pipeline to which the component belongs.

## Syntax

``` c++
  
HRESULT IPipelineContext::get_PipelineID(  
GUID*  
PipelineID  
);  
  
```

``` vb
  
Property PipelineID
() As GUID  
```

#### Parameters

*PipelineID*  
\[out,retval\] Globally unique identifier (GUID) used to return the pipeline ID.

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


