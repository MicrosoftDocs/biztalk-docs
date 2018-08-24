---
title: IBaseComponent.Description Property (COM)
TOCTitle: IBaseComponent.Description Property (COM)
ms:assetid: e4387905-2f54-48cc-a0d0-681f0f85ca4c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561597(v=BTS.80)
ms:contentKeyID: 51532994
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseComponent.Description Property (COM)

 

Gets the component description.

## Syntax

``` c++
  
HRESULT IBaseComponent::get_Description(  
BSTR*  
Description  
);  
  
```

``` vb
  
Property Description
() As String  
  
```

#### Parameters

*Description*  
\[out,retval\] String used to return the description of the component.

None.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

Not applicable.

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

[IBaseComponent Interface (COM)](ibasecomponent-interface-com.md)  
[IBaseComponent Members (COM)](ibasecomponent-members-com.md)

