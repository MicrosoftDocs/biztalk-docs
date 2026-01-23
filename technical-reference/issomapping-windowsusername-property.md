---
description: "Learn more about: ISSOMapping.WindowsUserName Property"
title: ISSOMapping.WindowsUserName Property
TOCTitle: ISSOMapping.WindowsUserName Property
ms:assetid: af1ef5a6-0019-41c9-9a2d-bf1e6087667d
ms:mtpsurl: https://msdn.microsoft.com/library/Aa705197(v=BTS.80)
ms:contentKeyID: 51530544
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
dev_langs:
- c++
- vb
---

# ISSOMapping.WindowsUserName Property

 

The **WindowsUserName** property specifies the Microsoft Windows user name.

**Get** method:

## Syntax

``` c++
  
HRESULT ISSOMapping::get_WindowsUserName(BSTR*WindowsUserName);  
HRESULT ISSOMapping::put_WindowsUserName(BSTR WindowsUserName);  
```

``` vb
  
Property WindowsUserName
() As String  
```

#### Parameters

`WindowsUserName`  
\[in\] When putting the property, a string that contains the Windows user name. \[out, retval\] When getting the property, a string used to return the Windows user name.

None.

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
<td>S_OK</td>
<td>The method succeeded.</td>
</tr>
<tr class="even">
<td>E_ACCESSDENIED</td>
<td>Access is denied to the caller.</td>
</tr>
<tr class="odd">
<td>E_INVALIDARG</td>
<td>An invalid parameter was detected.</td>
</tr>
</tbody>
</table>


## Requirements

**Platforms:**  Windows

## See Also

[ISSOMapping Interface (COM)](issomapping-interface-com.md)  
[ISSOMapping Members](issomapping-members.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

