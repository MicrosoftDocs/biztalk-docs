---
description: "Learn more about: ISSOMapper.SetWindowsPassword Method"
title: ISSOMapper.SetWindowsPassword Method
TOCTitle: ISSOMapper.SetWindowsPassword Method
ms:assetid: d02c4959-4c6e-4f94-945f-1451bc78c5de
ms:mtpsurl: https://msdn.microsoft.com/library/Aa771929(v=BTS.80)
ms:contentKeyID: 51531483
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
dev_langs:
- c++
- vb
---

# ISSOMapper.SetWindowsPassword Method

 

The **SetWindowsPassword** method sets the Microsoft Windows password. This method is not currently implemented.

## Syntax

``` c++
  
HRESULT SetWindowsPassword(  
BSTR bstrWindowsPassword  
);  
```

``` vb
  
Sub SetWindowsPassword(  
bstrWindowsPassword As String  
)  
```

#### Parameters

`bstrWindowsPassword`  
\[in\] String that specifies the Windows password.

`bstrWindowsPassword`  
\[in\] String that specifies the Windows password.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.

Not applicable.

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
<td>E_NOTIMPL</td>
<td>The method is not implemented.</td>
</tr>
</tbody>
</table>


## Requirements

**Platforms:**  Windows

## See Also

[ISSOMapper Interface (COM)](issomapper-interface-com.md)  
[ISSOMapper Members](issomapper-members.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

