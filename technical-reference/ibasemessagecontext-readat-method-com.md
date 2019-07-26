---
title: IBaseMessageContext.ReadAt Method (COM)
TOCTitle: IBaseMessageContext.ReadAt Method (COM)
ms:assetid: f4aaa5be-7d8e-4e84-8368-229b22410d45
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561940(v=BTS.80)
ms:contentKeyID: 51533419
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessageContext.ReadAt Method (COM)

 

Gets the property from the message context by index.

## Syntax

``` c++
  
    HRESULT IBaseMessageContext::ReadAt(   
Long index,BSTR* pbstrName,BSTR* pbstrNamespace,VARIANT *pVar);  
```

``` vb
  
      Function ReadAt( _   
index As Long, _pbstrName As String, _pbstrNamespace As String _) As Variant  
```

#### Parameters

*index*  
\[in\] The position of the property to read.

*index*  
The position of the property to read.

*pbstrName*  
\[in\] String that contains the property name.

*pbstrName*  
**String** that contains the property name.

*pbstrNamespace*  
\[in\] String that contains the property namespace.

*pbstrNamespace*  
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

