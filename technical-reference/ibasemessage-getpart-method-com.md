---
description: "Learn more about: IBaseMessage.GetPart Method (COM)"
title: IBaseMessage.GetPart Method (COM)
TOCTitle: IBaseMessage.GetPart Method (COM)
ms:assetid: 4797896e-dd93-482d-a786-959240fd9522
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559912(v=BTS.80)
ms:contentKeyID: 51527772
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessage.GetPart Method (COM)

 

Accesses the message parts.

## Syntax

``` c++
  
        HRESULT IBaseMessage::GetPart(  
        BSTR  
        bstrPartName,  
IBaseMessagePart**ppPart);  
```

``` vb
  
Function GetPart(  
bstrPartName  
 As String  
) As IBaseMessagePart  
  
```

#### Parameters

*bstrPartName*  
\[in\] String that contains the part name.

*bstrPartName*  
**String** that contains the part name.

*ppPart*  
\[out,retval\] Pointer to hold the reference to the returned **IBaseMessagePart** object/interface, which will contain the part.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns a [IBaseMessagePart](ibasemessagepart-interface-com.md) containing the part.

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

