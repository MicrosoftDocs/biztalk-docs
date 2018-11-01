---
title: IDocumentSpec.GetSchemaCollection Method (COM)
TOCTitle: IDocumentSpec.GetSchemaCollection Method (COM)
ms:assetid: bcc0f179-89c7-455c-996c-be9fb9590d02
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578374(v=BTS.80)
ms:contentKeyID: 51530934
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IDocumentSpec.GetSchemaCollection Method (COM)

 

Gets the schema collection.

## Syntax

``` c++
  
HRESULT IDocumentSpec::GetSchemaCollection(  
IUnknown**  
ppRet  
);  
  
```

``` vb
  
Function GetSchemaCollection
() As IUnknown  
  
```

#### Parameters

*ppRet*  
\[out,retval\] Address of a pointer to receive an **IUnknown** interface, which will contain the XML schema collection that contains the schema collection.

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

