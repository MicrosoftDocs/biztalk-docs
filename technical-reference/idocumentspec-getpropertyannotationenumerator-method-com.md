---
title: IDocumentSpec.GetPropertyAnnotationEnumerator Method (COM)
TOCTitle: IDocumentSpec.GetPropertyAnnotationEnumerator Method (COM)
ms:assetid: aaab489c-ce2d-4e07-90c6-c884f9316ed7
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577982(v=BTS.80)
ms:contentKeyID: 51530368
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IDocumentSpec.GetPropertyAnnotationEnumerator Method (COM)

 

Gets the property annotation.

## Syntax

``` c++
  
HRESULT IDocumentSpec::GetPropertyAnnotationEnumerator(  
IUnknown**  
ppRet  
);  
  
```

``` vb
  
Function GetPropertyAnnotationEnumerator
() As IUnknown  
  
```

#### Parameters

*ppRet*  
\[out,retval\] Address of a pointer to receive an **IUnknown** interface, which will contain the property annotation.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns a **IUnknown** that contains the transaction that the Messaging Engine will use in agent interactions. This parameter may be **NULL**.

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
</tbody>
</table>


## Remarks

The BizTalk Server Messaging Engine calls this method prior to pushing messages into the batch.

## Requirements

**Platforms:**  Windows

## See Also

[IDocumentSpec Interface (COM)](idocumentspec-interface-com.md)  
[IDocumentSpec Members (COM)](idocumentspec-members-com.md)

