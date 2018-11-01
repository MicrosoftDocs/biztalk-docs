---
title: IBaseMessagePart.PartProperties Property (COM)
TOCTitle: IBaseMessagePart.PartProperties Property (COM)
ms:assetid: 4cd4fe67-53ed-447e-85c9-af022809cb73
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560045(v=BTS.80)
ms:contentKeyID: 51527885
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessagePart.PartProperties Property (COM)

 

Contains one or more properties that describe the part data or contain custom information about the part.

## Syntax

``` c++
  
HRESULT IBaseMessagePart::get_PartProperties(  
IBasePropertyBag**  
PartProperties  
);  
HRESULT IBaseMessagePart::put_PartProperties(  
IBasePropertyBag*  
PartProperties  
);  
  
```

``` vb
  
Property PartProperties
() As IBasePropertyBag  
  
```

#### Parameters

*PartProperties*  
\[in\] When putting the property, an **IBasePropertyBag** that contains the part properties. \[out, retval\] When getting the property, an **IBasePropertyBag** used to return the part properties.

None.

## Return Value

These methods return an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

Not applicable.

## Error Values

These methods return an HRESULT containing one of the values in the following table.

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


## Remarks

Some of the properties contained in this property bag are also available on the part itself.

## Requirements

**Platforms:**  Windows

## See Also

[IBaseMessagePart Interface (COM)](ibasemessagepart-interface-com.md)  
[IBaseMessagePart Members (COM)](ibasemessagepart-members-com.md)

