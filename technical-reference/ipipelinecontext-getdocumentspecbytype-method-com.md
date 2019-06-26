---
title: IPipelineContext.GetDocumentSpecByType Method (COM)
TOCTitle: IPipelineContext.GetDocumentSpecByType Method (COM)
ms:assetid: 34d689c9-6dd7-48c0-a41d-a63730fc0e1c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559541(v=BTS.80)
ms:contentKeyID: 51527232
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IPipelineContext.GetDocumentSpecByType Method (COM)

 

Gets the [IDocumentSpec](idocumentspec-interface-com.md) object for specified document type.

## Syntax

``` c++
  
        HRESULT IPipelineContext::GetDocumentSpecByType(  
        BSTR  
        DocType,  
IDocumentSpec**ppRet);  
```

``` vb
  
Function GetDocumentSpecByType(  
DocType  
 As String  
) As IDocumentSpec  
  
```

#### Parameters

*DocType*  
\[in\] String that contains the document type.

*DocType*  
**String** that contains the document type.

*ppRet*  
\[out,retval\] Pointer to hold the reference to the returned **IDocumentSpec** object/interface.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it the **IDocumentSpec** containing the document with the specified type.

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

[IPipelineContext Interface (COM)](ipipelinecontext-interface-com.md)  
[IPipelineContext Members (COM)](ipipelinecontext-members-com.md)

