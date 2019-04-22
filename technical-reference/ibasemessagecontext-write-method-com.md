---
title: IBaseMessageContext.Write Method (COM)
TOCTitle: IBaseMessageContext.Write Method (COM)
ms:assetid: dc0e9c2f-43e8-470e-a285-86c4e7000f9e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561422(v=BTS.80)
ms:contentKeyID: 51532644
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessageContext.Write Method (COM)

 

Writes a property into the message context.

## Syntax

``` c++
  
         HRESULT IBaseMessageContext::Write(   
BSTR bstrName,   BSTR bstrNamespace,   Variant var);  
```

``` vb
  
      Sub Write( _   
bstrName As String, _bstrNamespace As String, _var As Variant _)  
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

*var*  
\[in\] Variant that contains the context property value.

*vare*  
**Variant** that contains context property value.

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

The written property is not being promoted.

## Requirements

**Platforms:**  Windows

## See Also

[IBaseMessageContext Interface (COM)](ibasemessagecontext-interface-com.md)  
[IBaseMessageContext Members (COM)](ibasemessagecontext-members-com.md)

