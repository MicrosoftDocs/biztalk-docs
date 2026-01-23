---
description: "Learn more about: IBaseMessagePart.PartID Property (COM)"
title: IBaseMessagePart.PartID Property (COM)
TOCTitle: IBaseMessagePart.PartID Property (COM)
ms:assetid: 2ee35a62-d72b-42d0-b9f2-4f33ec3acec0
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559431(v=BTS.80)
ms:contentKeyID: 51527069
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IBaseMessagePart.PartID Property (COM)

 

Gets the unique ID for the part.

## Syntax

``` c++
  
HRESULT IBaseMessagePart::get_PartID(  
GUID*  
PartID  
);  
  
```

``` vb
  
Property PartID
() As GUID  
```

#### Parameters

*PartID*  
\[out,retval\] Globally unique identifier (GUID) used to return the part ID.

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

[IBaseMessagePart Interface (COM)](ibasemessagepart-interface-com.md)  
[IBaseMessagePart Members (COM)](ibasemessagepart-members-com.md)

