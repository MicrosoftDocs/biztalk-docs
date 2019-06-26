---
title: IBasePropertyBag.Read Method (COM)
TOCTitle: IBasePropertyBag.Read Method (COM)
ms:assetid: 8f16bd8a-e7ba-4e47-afa0-b01ca47f2bd6
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561344(v=BTS.80)
ms:contentKeyID: 51529642
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBasePropertyBag.Read Method (COM)

 

Reads the value and type of the given property in the property bag.

## Syntax

``` c++
  
        HRESULT IBasePropertyBag::Read(  
        BSTR  
        bstrName,  
BSTRbstrNamespace,  
VARIANT*pVar);  
```

``` vb
  
        Function Read(  
        bstrName  
         As String,  
bstrNamespace As String) As Variant  
```

#### Parameters

*bstrName*  
\[in\] String that contains the name.

*bstrName*  
**String** that contains the name.

*bstrNamespace*  
\[in\] String that contains the namespace.

*bstrNamespace*  
**String** that contains the namespace.

*pVar*  
\[out,retval\] Pointer to a Variant used to return the message context property value.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns the message context property value.

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

[IBasePropertyBag Interface (COM)](ibasepropertybag-interface-com.md)  
[IBasePropertyBag Members (COM)](ibasepropertybag-members-com.md)

