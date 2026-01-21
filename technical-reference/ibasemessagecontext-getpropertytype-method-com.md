---
description: "Learn more about: IBaseMessageContext.GetPropertyType Method (COM)"
title: IBaseMessageContext.GetPropertyType Method (COM)
TOCTitle: IBaseMessageContext.GetPropertyType Method (COM)
ms:assetid: 49c3cb8b-0ab3-478f-9422-fcc2d09b74f3
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559966(v=BTS.80)
ms:contentKeyID: 51527817
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IBaseMessageContext.GetPropertyType Method (COM)

 

Gets the type of the property.

## Syntax

``` c++
  
        HRESULT IBaseMessageContext::GetPropertyType(  
        BSTR  
        bstrName,  
BSTRbstrNamespace,  
PropertyType*ppRet);  
```

``` vb
  
        Function GetPropertyType(  
        bstrName  
         As String,  
bstrNamespace As String) As PropertyType  
```

#### Parameters

*bstrName*  
\[in\] String that contains the property name.

*bstrName*  
**String** that contains the property name.

*bstrNamespace*  
\[in\] String that contains the property namespace.

*bstrNamespace*  
**String** that contains the property namespace.

*ppRet*  
\[out,retval\] Pointer to a **PropertyType**.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

**true** if the property has been marked for promotion; otherwise, **false**.

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

[IBaseMessageContext Interface (COM)](ibasemessagecontext-interface-com.md)  
[IBaseMessageContext Members (COM)](ibasemessagecontext-members-com.md)

