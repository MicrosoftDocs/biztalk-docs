---
description: "Learn more about: IBaseMessageContext.AddPredicate Method (COM)"
title: IBaseMessageContext.AddPredicate Method (COM)
TOCTitle: IBaseMessageContext.AddPredicate Method (COM)
ms:assetid: b1bd4386-86ab-4b58-af17-ad837a763c59
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578148(v=BTS.80)
ms:contentKeyID: 51530561
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessageContext.AddPredicate Method (COM)

 

Adds a message predicate to the message.

## Syntax

``` c++
  
        HRESULT IBaseMessageContext::AddPredicate(  
        BSTR  
        bstrName,  
BSTRbstrNamespace,  
VARIANTVar);  
```

``` vb
  
        Sub AddPredicate(  
        bstrName  
         As String,  
bstrNamespace As String,  
Var As Variant)  
```

#### Parameters

*bstrName*  
\[in\] String that contains the host property name.

*bstrName*  
**String** that contains the host property name.

*bstrNamespace*  
\[in\] String that contains the host property namespace.

*bstrNamespace*  
**String** that contains the host property namespace.

*Var*  
\[in\] Variant that contains the value to be matched against the host property value.

*Var*  
**Variant** that contains the value to be matched against the host property value.

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

The MessageBox only supports the equals operation for message predicates.

## Requirements

**Platforms:**  Windows

## See Also

[IBaseMessageContext Interface (COM)](ibasemessagecontext-interface-com.md)  
[IBaseMessageContext Members (COM)](ibasemessagecontext-members-com.md)

