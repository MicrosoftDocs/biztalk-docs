---
description: "Learn more about: IBaseMessageContext.Read Method (COM)"
title: IBaseMessageContext.Read Method (COM)
TOCTitle: IBaseMessageContext.Read Method (COM)
ms:assetid: 17da744e-c779-4765-b071-217eb08e782f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa558785(v=BTS.80)
ms:contentKeyID: 51526453
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference 
---

# IBaseMessageContext.Read Method (COM)

 

Gets the property value from the message context by the name-namespace pair.

## Syntax

``` c++
  
         HRESULT IBaseMessageContext::Read(   
BSTR bstrName,   BSTR bstrNamespace,VARIANT *pVar);  
```

``` vb
  
      Function Read( _   
bstrName As String, _bstrNamespace As String _) As Variant  
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

*pVar*  
\[out,retval\] Pointer to a Variant used to return the message context property value.

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


## Requirements

**Platforms:**  Windows

## See Also

[IBaseMessageContext Interface (COM)](ibasemessagecontext-interface-com.md)  
[IBaseMessageContext Members (COM)](ibasemessagecontext-members-com.md)

