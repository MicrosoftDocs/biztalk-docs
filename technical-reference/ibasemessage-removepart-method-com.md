---
description: "Learn more about: IBaseMessage.RemovePart Method (COM)"
title: IBaseMessage.RemovePart Method (COM)
TOCTitle: IBaseMessage.RemovePart Method (COM)
ms:assetid: e4dd1504-8101-4b3c-89e3-2b6e3b7fc3f4
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561612(v=BTS.80)
ms:contentKeyID: 51533013
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessage.RemovePart Method (COM)

 

Removes a part from the message.

## Syntax

``` c++
  
HRESULT IBaseMessage::RemovePart(  
BSTR  
bstrPartName  
);  
  
```

``` vb
  
Sub RemovePart(  
bstrPartName  
 As String  
)  
  
```

#### Parameters

*bstrPartName*  
\[in\] String that contains the part name.

*bstrPartName*  
**String** that contains the part name.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

None.

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

