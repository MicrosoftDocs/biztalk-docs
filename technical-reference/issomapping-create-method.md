---
description: "Learn more about: ISSOMapping.Create Method"
title: ISSOMapping.Create Method
TOCTitle: ISSOMapping.Create Method
ms:assetid: 3133f03a-0474-4e55-a8be-ca53f69144ef
ms:mtpsurl: https://msdn.microsoft.com/library/Aa770329(v=BTS.80)
ms:contentKeyID: 51527128
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
dev_langs:
- c++
- vb
---

# ISSOMapping.Create Method

 

The **Create** method creates the mapping.

## Syntax

``` c++
  
HRESULT Create(  
LONG lFlags  
);  
```

``` vb
  
Sub Create(  
lFlags As Long  
)  
```

#### Parameters

`lFlags`  
For the current release, *lFlags* can be set to SSO\_FLAG\_REFRESH only.

`lFlags`  
For the current release, *lFlags* can be set to SSO\_FLAG\_REFRESH only.

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

