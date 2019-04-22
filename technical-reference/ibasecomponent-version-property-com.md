---
title: IBaseComponent.Version Property (COM)
TOCTitle: IBaseComponent.Version Property (COM)
ms:assetid: 41d78d01-4fe8-4e76-8262-2c17330fd710
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559795(v=BTS.80)
ms:contentKeyID: 51527613
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseComponent.Version Property (COM)

 

Gets the component version.

## Syntax

``` c++
  
Version  
  
```

``` vb
```

## Parameters

*Version*  
\[out,retval\] String used to return the version of the component.

None.

## Return Values

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

