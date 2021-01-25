---
description: "Learn more about: IBaseMessagePart.GetOriginalDataStream Method (COM)"
title: IBaseMessagePart.GetOriginalDataStream Method (COM)
TOCTitle: IBaseMessagePart.GetOriginalDataStream Method (COM)
ms:assetid: 2359b2e5-e574-41a1-9f56-aaa117825a4a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559195(v=BTS.80)
ms:contentKeyID: 51526758
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessagePart.GetOriginalDataStream Method (COM)

 

Retrieves the original uncloned version of the part data stream.

## Syntax

``` c++
  
HRESULT IBaseMessagePart::GetOriginalDataStream(  
IStream**  
ppStream  
);  
  
```

``` vb
  
Function GetOriginalDataStream
() As IStream  
  
```

#### Parameters

*ppStream*  
\[out,retval\] Pointer to hold the reference to the returned **IStream** object/interface, which will contain the stream.

None.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns the uncloned version of the part data stream.

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


## Remarks

The component should ensure safe multithreaded access to the stream when using this method.

## Requirements

**Platforms:**  Windows

## See Also

[IBaseMessagePart Interface (COM)](ibasemessagepart-interface-com.md)  
[IBaseMessagePart Members (COM)](ibasemessagepart-members-com.md)

