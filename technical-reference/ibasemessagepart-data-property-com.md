---
description: "Learn more about: IBaseMessagePart.Data Property (COM)"
title: IBaseMessagePart.Data Property (COM)
TOCTitle: IBaseMessagePart.Data Property (COM)
ms:assetid: 463b8e0c-2fe5-4ac0-acc6-893f6ec0be98
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559876(v=BTS.80)
ms:contentKeyID: 51527674
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessagePart.Data Property (COM)

 

Accesses the part data.

## Syntax

``` c++
  
HRESULT IBaseMessagePart::get_Data(  
  IStream** Data  
);  
HRESULT IBaseMessagePart::put_Data(IStream*Data);  
```

``` vb
  
Property Data
() As IStream  
  
```

#### Parameters

*Data*  
\[in\] When putting the property, an **IStream** that contains the part data. \[out,retval\] When getting the property, an **IStream** used to return the part data.

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

For messages delivered by the Messaging Engine, the part data for the attachment parts are loaded only on demand.

## Requirements

**Platforms:**  Windows

## See Also

[IBaseMessagePart Interface (COM)](ibasemessagepart-interface-com.md)  
[IBaseMessagePart Members (COM)](ibasemessagepart-members-com.md)

