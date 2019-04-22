---
title: IBaseMessageFactory.CreateMessage Method (COM)
TOCTitle: IBaseMessageFactory.CreateMessage Method (COM)
ms:assetid: b30e0ea9-9861-42e8-8a9b-13167686c930
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578181(v=BTS.80)
ms:contentKeyID: 51530649
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessageFactory.CreateMessage Method (COM)

 

Creates a BizTalk message.

## Syntax

``` c++
  
ppMsg  
  
```

``` vb
```

## Parameters

*ppMsg*  
\[out,retval\] Pointer to hold the reference to the returned **IBaseMessage** object/interface, which will contain the message.

None.

## Return Values

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns the **IBaseMessage** containing the message.

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

