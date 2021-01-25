---
description: "Learn more about: IBaseMessage.GetSize Method (COM)"
title: IBaseMessage.GetSize Method (COM)
TOCTitle: IBaseMessage.GetSize Method (COM)
ms:assetid: ed17043f-112c-40cc-951f-dbc663979822
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561773(v=BTS.80)
ms:contentKeyID: 51533214
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessage.GetSize Method (COM)

 

Gets the size of the message.

## Syntax

``` c++
  
        HRESULT IBaseMessage::GetSize(  
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
\[out\] Pointer to a **ULARGE\_INTEGER** used to return the size of the message.

*pVal*  
ULARGE\_INTEGER used to return the size of the message.

*pfImplemented*  
\[out, retval\] Pointer to a Boolean used to return the results of the counting operation. **true** if the [IBaseMessage](ibasemessage-interface-com.md) object can determine the size; otherwise, **false**.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns **true** if the [IBaseMessage](ibasemessage-interface-com.md) object can determine the size; otherwise, **false**.

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

[IBaseMessage Interface (COM)](ibasemessage-interface-com.md)  
[IBaseMessage Members (COM)](ibasemessage-members-com.md)

