---
title: IDocumentSpec.DocType Property (COM)
TOCTitle: IDocumentSpec.DocType Property (COM)
ms:assetid: ec9331a5-1d05-4181-98e0-fe781cf74515
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561765(v=BTS.80)
ms:contentKeyID: 51533204
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IDocumentSpec.DocType Property (COM)

 

Gets the type of the document.

## Syntax

``` c++
  
HRESULT IDocumentSpec::get_DocType(  
BSTR*  
DocType  
);  
  
```

``` vb
  
Property DocType
() As String  
  
```

#### Parameters

*DocType*  
\[out,retval\] String used to return the document type.

None.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

Not applicable.

## Error Values

This method returns an HRESULT containing one of the values in the following table.

This property indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.

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
<td>The property was successfully obtained or written.</td>
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

[IDocumentSpec Interface (COM)](idocumentspec-interface-com.md)  
[IDocumentSpec Members (COM)](idocumentspec-members-com.md)  
[Using the Parsing and Serializing Engines](https://msdn.microsoft.com/library/aa577963\(v=bts.80\))

