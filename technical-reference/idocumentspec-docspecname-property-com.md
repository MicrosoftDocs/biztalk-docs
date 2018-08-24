---
title: IDocumentSpec.DocSpecName Property (COM)
TOCTitle: IDocumentSpec.DocSpecName Property (COM)
ms:assetid: a21fdd1d-04ec-4a32-9d4f-2162c786cb66
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577808(v=BTS.80)
ms:contentKeyID: 51530127
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IDocumentSpec.DocSpecName Property (COM)

 

Gets the specification name of the current document.

## Syntax

``` c++
  
HRESULT IDocumentSpec::get_DocSpecName(  
BSTR*  
DocSpecName  
);  
  
```

``` vb
  
Property DocSpecName
() As String  
  
```

#### Parameters

*DocSpecName*  
\[out,retval\] String used to return the schema name.

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
[Using the Parsing and Serializing Engines](https://msdn.microsoft.com/en-us/library/aa577963\(v=bts.80\))

