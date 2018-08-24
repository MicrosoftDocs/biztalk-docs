---
title: IBaseMessagePart.ContentType Property (COM)
TOCTitle: IBaseMessagePart.ContentType Property (COM)
ms:assetid: e02744b5-713e-47bb-9b6f-ac074527a338
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561511(v=BTS.80)
ms:contentKeyID: 51532884
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessagePart.ContentType Property (COM)

 

Accesses the content type property for the part.

## Syntax

``` c++
  
            HRESULT IBaseMessagePart::get_ContentType(  
            BSTR*  
            ContentType  
            );   
HRESULT IBaseMessagePart::put_ContentType(BSTRContentType);  
```

``` vb
  
Property ContentType
() As String  
  
```

#### Parameters

*ContentType*  
\[in\] When putting the property, a string that contains the content type. \[out, retval\] When getting the property, a string used to return the content type.

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

This property is also available on the [PartProperties](ibasemessagepart-partproperties-property-com.md) property, the property bag for the part.

## Requirements

**Platforms:**  Windows

## See Also

[IBaseMessagePart Interface (COM)](ibasemessagepart-interface-com.md)  
[IBaseMessagePart Members (COM)](ibasemessagepart-members-com.md)

