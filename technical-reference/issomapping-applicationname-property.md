---
title: ISSOMapping.ApplicationName Property
TOCTitle: ISSOMapping.ApplicationName Property
ms:assetid: ef4c7235-0050-41ad-8fb3-70e7ffe28def
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa705611(v=BTS.80)
ms:contentKeyID: 51533293
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOMapping.ApplicationName Property

 

The **ApplicationName** property specifies the name of the application.

## Syntax

``` c++
  
HRESULT ISSOMapping::get_ApplicationName(  
BSTR* ApplicationName  
);  
HRESULT ISSOMapping::put_ApplicationName(  
BSTR ApplicationName  
);  
```

``` vb
  
Property ApplicationName
() As String  
  
```

#### Parameters

`ApplicationName`  
\[in\] When putting the property, a string that contains the application name. \[out, retval\] When getting the property, a string used to return the application name.

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
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/en-us/library/aa704508\(v=bts.80\))

