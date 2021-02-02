---
description: "Learn more about: IBTTransportBatch.ResourceTracker Property (COM)"
title: IBTTransportBatch.ResourceTracker Property (COM)
TOCTitle: IBTTransportBatch.ResourceTracker Property (COM)
ms:assetid: 1d175ff6-7582-48fe-8707-6eb59a2d61eb
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559087(v=BTS.80)
ms:contentKeyID: 51526593
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportBatch.ResourceTracker Property (COM)

 

This property is not supported and returns a value of E\_NOTIMPL.

## Syntax

``` c++
  
HRESULT IBTTransportBatch::IResourceTracker(  
ResourceTracker  
resourceTracker  
);  
  
```

``` vb
  
Property ResourceTracker
() As IResourceTracker  
  
```

## Remarks

**Parameters**

*bstrCorrelationToken*  
\[out,retval\] Not implemented.

None.

**Return Values**

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

None.

**Error Values**

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


**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportBatch Interface (COM)](ibttransportbatch-interface-com.md)  
[IBTTransportBatch Members (COM)](ibttransportbatch-members-com.md)

