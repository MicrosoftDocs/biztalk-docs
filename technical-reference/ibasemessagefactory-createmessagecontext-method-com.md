---
title: IBaseMessageFactory.CreateMessageContext Method (COM)
TOCTitle: IBaseMessageFactory.CreateMessageContext Method (COM)
ms:assetid: 72683e61-af87-4059-80f5-9c429a5bba5a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560799(v=BTS.80)
ms:contentKeyID: 51528907
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessageFactory.CreateMessageContext Method (COM)

 

Creates a BizTalk message context.

## Syntax

``` c++
  
HRESULT IBaseMessageFactory::CreateMessageContext(  
IBaseMessageContext**  
ppContext  
);  
  
```

``` vb
  
Function CreateMessageContext
() As IBaseMessageContext  
  
```

#### Parameters

*ppContext*  
\[out,retval\] Pointer to hold the reference to the returned **IBaseMessageContext** object/interface, which will contain the context.

None.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns the **IBaseMessageContext** containing the message context.

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

[IBaseMessageFactory Interface (COM)](ibasemessagefactory-interface-com.md)  
[IBaseMessageFactory Members (COM)](ibasemessagefactory-members-com.md)

