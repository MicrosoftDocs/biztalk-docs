---
title: IDocumentSpec.GetBodyPath Method (COM)
TOCTitle: IDocumentSpec.GetBodyPath Method (COM)
ms:assetid: 31bb56aa-2f8e-44fe-a046-8d572d32198c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559485(v=BTS.80)
ms:contentKeyID: 51527146
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IDocumentSpec.GetBodyPath Method (COM)

 

Returns the XML Path (XPath) to the node in the document where the body part begins.

## Syntax

``` c++
  
HRESULT IDocumentSpec::GetBodyPath(  
BSTR*  
pBodyPath  
);  
  
```

``` vb
  
Function GetBodyPath
() As String  
  
```

#### Parameters

*pBodyPath*  
\[out,retval\] For an envelope schema, this method returns the XPath to the node in the document where the body part begins. For a document schema, this method returns **null**.

None.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

For an envelope schema, this property contains the XPath to the node in the document where the body part begins. For a schema, this property will be **Null**.

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

[IDocumentSpec Interface (COM)](idocumentspec-interface-com.md)  
[IDocumentSpec Members (COM)](idocumentspec-members-com.md)  
[Using the Parsing and Serializing Engines](https://msdn.microsoft.com/library/aa577963\(v=bts.80\))

