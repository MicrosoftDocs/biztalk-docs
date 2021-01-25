---
description: "Learn more about: IBaseMessageContext.CountProperties Method (COM)"
title: IBaseMessageContext.CountProperties Method (COM)
TOCTitle: IBaseMessageContext.CountProperties Method (COM)
ms:assetid: c6a0493b-a079-49a2-8f6b-c858ec3429f4
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547924(v=BTS.80)
ms:contentKeyID: 51531207
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessageContext.CountProperties Method (COM)

 

Gets the number of properties in the message context.

## Syntax

``` c++
  
cCount  
```

``` vb
  
cCount  
  
```

## Parameters

*cCount*  
\[out\] Pointer to a **ULONG** used to return the count.

*cCount*  
ULONG used to return the count.

## Return Values

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

