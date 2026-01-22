---
description: "Learn more about: IBaseMessageContext.Promote Method (COM)"
title: IBaseMessageContext.Promote Method (COM)
TOCTitle: IBaseMessageContext.Promote Method (COM)
ms:assetid: fd845a40-1de1-48b8-9d3e-e8ce7db91428
ms:mtpsurl: https://msdn.microsoft.com/library/Aa562128(v=BTS.80)
ms:contentKeyID: 51533710
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IBaseMessageContext.Promote Method (COM)

 

Promotes the property into the message context.

## Syntax

``` c++
  
        HRESULT IBaseMessageContext::Promote(  
        BSTR  
        bstrName,  
BSTRbstrNamespace,  
VARIANTVar);  
```

``` vb
  
        Sub Promote(  
        bstrName  
         As String,  
bstrNamespace As String,  
Var As Variant)  
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

*Var*  
\[in\] Variant that contains the context property value.

*Var*  
**Variant** that contains the context property value.

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


## Remarks

When the message is published, the promoted properties are extracted from the context and written to the database as clear values. All the promoted properties for a message are used for subscription evaluation.

## Requirements

**Platforms:**  Windows

## See Also

[IBaseMessageContext Interface (COM)](ibasemessagecontext-interface-com.md)  
[IBaseMessageContext Members (COM)](ibasemessagecontext-members-com.md)

