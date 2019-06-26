---
title: IBaseMessagePart.GetSize Method (COM)
TOCTitle: IBaseMessagePart.GetSize Method (COM)
ms:assetid: ca648ba0-707a-4e1d-860b-2882b30c004f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547994(v=BTS.80)
ms:contentKeyID: 51531303
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessagePart.GetSize Method (COM)

 

Retrieves the size of the part.

## Syntax

``` c++
  
        HRESULT IBaseMessagePart::GetSize(  
        ULARGE_INTEGER*  
        pVal,  
BOOL*pfImplemented);  
```

``` vb
  
Function GetSize(  
pVal  
 As ULARGE_INTEGER  
) As Boolean  
  
```

#### Parameters

*pVal*  
\[out\] Pointer to a **ULARGE\_INTEGER** used to return the size of the object.

*pVal*  
ULARGE\_INTEGER used to return the size of the object.

*pfImplemented*  
\[out, retval\] Pointer to a Boolean used to return the information if the message size can be determined. **true** if the [IBaseMessage](ibasemessage-interface-com.md) object can determine the size; otherwise, **false**.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

**true** if the [IBaseMessage](ibasemessage-interface-com.md) object can determine the size; otherwise, **false**.

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


## Remarks

If the message has already been persisted and the data is unchangeable, then this value is a stored value. If the message is new, then the value is calculated at the time of the call. For new messages, you can get different values depending on when in the pipeline or schedule you call into the message because the data can change.

## Requirements

**Platforms:**  Windows

## See Also

[IBaseMessagePart Interface (COM)](ibasemessagepart-interface-com.md)  
[IBaseMessagePart Members (COM)](ibasemessagepart-members-com.md)

