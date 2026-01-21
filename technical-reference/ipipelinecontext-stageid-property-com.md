---
description: "Learn more about: IPipelineContext.StageID Property (COM)"
title: IPipelineContext.StageID Property (COM)
TOCTitle: IPipelineContext.StageID Property (COM)
ms:assetid: e89b583d-3d50-499c-b1e2-f046ab330704
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561683(v=BTS.80)
ms:contentKeyID: 51533091
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IPipelineContext.StageID Property (COM)

Â 

Gets the ID of the stage in the pipeline.

## Syntax

``` c++
  
HRESULT IPipelineContext::get_StageID(  
GUID*  
StageID  
);  
  
```

``` vb
  
Property StageID
() As GUID  
```

#### Parameters

*StageID*  
\[out,retval\] Globally unique identifier (GUID) used to return the stage ID.

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

**Platforms:**Â Â Windows

## See Also

[IPipelineContext Interface (COM)](ipipelinecontext-interface-com.md)  
[IPipelineContext Members (COM)](ipipelinecontext-members-com.md)


