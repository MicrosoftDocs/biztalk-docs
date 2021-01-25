---
description: "Learn more about: IBaseComponent.Name Property (COM)"
title: IBaseComponent.Name Property (COM)
TOCTitle: IBaseComponent.Name Property (COM)
ms:assetid: 2ab91ce2-7bee-4bc2-bbf8-c9e9b3393c81
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559341(v=BTS.80)
ms:contentKeyID: 51527015
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseComponent.Name Property (COM)

 

Gets the component name.

## Syntax

``` c++
  
HRESULT IBaseComponent::get_Name(  
BSTR*  
Name  
);  
  
```

``` vb
  
Property Name
() As String  
  
```

#### Parameters

*Name*  
\[out,retval\] String used to return the name of the component.

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

