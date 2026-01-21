---
description: "Learn more about: IPipelineContext.GetDocumentSpecByName Method (COM)"
title: IPipelineContext.GetDocumentSpecByName Method (COM)
TOCTitle: IPipelineContext.GetDocumentSpecByName Method (COM)
ms:assetid: 5bdf0e8f-32bb-4bef-8245-3b9518cd182a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560353(v=BTS.80)
ms:contentKeyID: 51528294
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IPipelineContext.GetDocumentSpecByName Method (COM)

Â 

Gets the [IDocumentSpec](idocumentspec-interface-com.md) object for the specified document name.

## Syntax

``` c++
  
        HRESULT IPipelineContext::GetDocumentSpecByName(  
        BSTR  
        DocSpecName,  
IDocumentSpec**ppRet);  
```

``` vb
  
Function GetDocumentSpecByName(  
DocSpecName  
 As String  
) As IDocumentSpec  
  
```

#### Parameters

*DocSpecName*  
\[in\] String that contains the schema name.

*DocSpecName*  
**String** that contains the schema name.

*ppRet*  
\[out,retval\] Pointer to hold the reference to the returned **IDocumentSpec** object/interface.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns the **IDocumentSpec** containing the document with the specified name.

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

**Platforms:**Â Â Windows

## See Also

[IPipelineContext Interface (COM)](ipipelinecontext-interface-com.md)  
[IPipelineContext Members (COM)](ipipelinecontext-members-com.md)


