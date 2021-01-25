---
description: "Learn more about: IBaseMessageFactory.CreateMessagePart Method (COM)"
title: IBaseMessageFactory.CreateMessagePart Method (COM)
TOCTitle: IBaseMessageFactory.CreateMessagePart Method (COM)
ms:assetid: 5e9e0d87-2800-4f2d-a907-171c9ac4afad
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560409(v=BTS.80)
ms:contentKeyID: 51528367
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessageFactory.CreateMessagePart Method (COM)

 

Creates a BizTalk message part.

## Syntax

``` c++
  
HRESULT IBaseMessageFactory::CreateMessagePart(  
IBaseMessagePart**  
ppPart  
);  
  
```

``` vb
  
Function CreateMessagePart
() As IBaseMessagePart  
  
```

#### Parameters

*ppPart*  
\[out,retval\] Pointer to hold the reference to the returned **IBaseMessagePart** object/interface, which will contain the part.

None.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns the **IBaseMessagePart** containing the message part.

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

