---
title: IPipelineContext.ComponentIndex Property (COM)
TOCTitle: IPipelineContext.ComponentIndex Property (COM)
ms:assetid: f242b9c5-7b50-4139-8d16-cd7bc6ae7ea5
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561892(v=BTS.80)
ms:contentKeyID: 51533359
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IPipelineContext.ComponentIndex Property (COM)

 

Gets the index of the current component in the stage.

## Syntax

``` c++
  
HRESULT IPipelineContext::get_ComponentIndex(  
LONG*  
ComponentIndex  
);  
  
```

``` vb
  
Property ComponentIndex
() As Long  
  
```

#### Parameters

*ComponentIndex*  
\[out,retval\] Integer used to return the component index.

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

