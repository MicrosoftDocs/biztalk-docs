---
title: IBaseMessageFactory.CreatePropertyBag Method (COM)
TOCTitle: IBaseMessageFactory.CreatePropertyBag Method (COM)
ms:assetid: f8861750-ae0d-4076-9e24-92fd0ed8e732
ms:mtpsurl: https://msdn.microsoft.com/library/Aa562015(v=BTS.80)
ms:contentKeyID: 51533515
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessageFactory.CreatePropertyBag Method (COM)

 

Creates a property bag for BizTalk message part.

## Syntax

``` c++
  
HRESULT IBaseMessageFactory::CreatePropertyBag(  
IBasePropertyBag**  
ppPropBag  
);  
  
```

``` vb
  
Function CreatePropertyBag
() As IBasePropertyBag  
  
```

#### Parameters

*ppPropBag*  
\[out,retval\] Pointer to hold the reference to the returned **IBasePropertyBag** object/interface, which will contain the property bag.

None.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns the **IBasePropertyBag** containing the context properties of the message.

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

