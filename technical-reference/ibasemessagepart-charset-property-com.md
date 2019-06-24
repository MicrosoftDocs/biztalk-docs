---
title: IBaseMessagePart.Charset Property (COM)
TOCTitle: IBaseMessagePart.Charset Property (COM)
ms:assetid: 205422d8-d396-4783-b849-a086946bf93e
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559144(v=BTS.80)
ms:contentKeyID: 51526691
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessagePart.Charset Property (COM)

 

Accesses the character set property for the part.

## Syntax

``` c++
  
            HRESULT IBaseMessagePart::get_Charset(  
            BSTR*  
            Charset  
            );   
HRESULT IBaseMessagePart::put_Charset(BSTRCharset);  
```

``` vb
  
Property Charset
() As String  
  
```

#### Parameters

*Charset*  
\[in\] When putting the property, a string that contains the character set. \[out, retval\] When getting the property, a string used to return the character set.

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

This property is also available in the [PartProperties](ibasemessagepart-partproperties-property-com.md) property, the property bag for the part.

## Requirements

**Platforms:**  Windows

## See Also

[IBaseMessagePart Interface (COM)](ibasemessagepart-interface-com.md)  
[IBaseMessagePart Members (COM)](ibasemessagepart-members-com.md)

