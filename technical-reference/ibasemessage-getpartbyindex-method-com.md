---
title: IBaseMessage.GetPartByIndex Method (COM)
TOCTitle: IBaseMessage.GetPartByIndex Method (COM)
ms:assetid: 5d49630b-6d5c-481c-aff5-91385cac232c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560385(v=BTS.80)
ms:contentKeyID: 51528334
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessage.GetPartByIndex Method (COM)

 

Retrieves a part and its name by supplying the part index.

## Syntax

``` c++
  
        HRESULT IBaseMessage::GetPartByIndex(  
        LONG  
        index,  
BSTR*pbstrPartName,  
IBaseMessagePart**ppPart);  
```

``` vb
  
        Function GetPartByIndex(  
        index  
         As Long,  
pbstrPartName As String) As IBaseMessagePart  
```

#### Parameters

*index*  
\[in\] Integer that contains the index.

*index*  
**Long** that contains the index.

*pbstrPartName*  
\[out\] Pointer to a string used to return the part name.

*pbstrPartName*  
**String** used to return the part name.

*ppPart*  
\[out,retval\] Pointer to hold the reference to the returned **IBaseMessagePart** object/interface, which will contain the part.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns an [IBaseMessagePart](ibasemessagepart-interface-com.md) containing the message part.

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

This method is useful for enumerating all the parts within a message.

## Requirements

**Platforms:**  Windows

## See Also

[IBaseMessage Interface (COM)](ibasemessage-interface-com.md)  
[IBaseMessage Members (COM)](ibasemessage-members-com.md)

