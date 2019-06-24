---
title: IComponentUI.Validate Method (COM)
TOCTitle: IComponentUI.Validate Method (COM)
ms:assetid: 99f52e7b-37cc-4c69-8f88-f92524577fbf
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577504(v=BTS.80)
ms:contentKeyID: 51529934
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IComponentUI.Validate Method (COM)

 

Verifies that all of the configuration properties are set correctly.

## Syntax

``` c++
  
HRESULT IComponentUI::Validate(  
IUnknown**  
ppEnum  
);  
  
```

``` vb
  
Function Validate
() As IUnknown  
  
```

#### Parameters

*ppEnum*  
\[out,retval\] Address of a pointer to receive an **IUnknown** interface, which will contain the enumeration.

None.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

None.

## Remarks

This method is called by the Pipeline Designer prior to pipeline compilation.

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

[IComponentUI Interface (COM)](icomponentui-interface-com.md)

