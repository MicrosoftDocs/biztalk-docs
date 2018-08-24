---
title: IComponentUI.Icon Property (COM)
TOCTitle: IComponentUI.Icon Property (COM)
ms:assetid: 4ad8b610-4b75-451d-9452-c5fe69fdc1b1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559986(v=BTS.80)
ms:contentKeyID: 51527842
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IComponentUI.Icon Property (COM)

 

Provides the icon that is associated with this component.

## Syntax

``` c++
  
HRESULT IComponentUI::get_Icon(  
IPicture**  
Icon  
);  
  
```

``` vb
  
Property Icon
() As IPicture  
  
```

#### Parameters

*Icon*  
\[out,retval\] **IPicture** used to return the icon.

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

[IComponentUI Interface (COM)](icomponentui-interface-com.md)

