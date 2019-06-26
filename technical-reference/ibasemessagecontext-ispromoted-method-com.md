---
title: IBaseMessageContext.IsPromoted Method (COM)
TOCTitle: IBaseMessageContext.IsPromoted Method (COM)
ms:assetid: 48b76ff7-f945-4dfb-9e3d-58a1276e3d16
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559933(v=BTS.80)
ms:contentKeyID: 51527749
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessageContext.IsPromoted Method (COM)

 

Enables the component to determine whether a property has already been marked for promotion in the message context.

## Syntax

``` c++
  
    bstrName,  
bstrNamespace,  
pbPromotionFlag  
```

``` vb
  
    bstrName  
      ,  
bstrNamespace  
```

## Parameters

*bstrName*  
\[in\] String that contains the property name.

*bstrName*  
**String** that contains the property name.

*bstrNamespace*  
\[in\] String that contains the property namespace.

*bstrNamespace*  
**String** that contains the property namespace.

*pbPromotionFlag*  
\[out,retval\] Pointer to a Boolean used to return the promotion flag. **true** if the property has been marked for promotion; otherwise, **false**.

## Return Values

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

