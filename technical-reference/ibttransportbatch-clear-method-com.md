---
description: "Learn more about: IBTTransportBatch.Clear Method (COM)"
title: IBTTransportBatch.Clear Method (COM)
TOCTitle: IBTTransportBatch.Clear Method (COM)
ms:assetid: 2f54feaa-86d2-4c69-87b7-c7a7e5d321fc
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559437(v=BTS.80)
ms:contentKeyID: 51527081
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportBatch.Clear Method (COM)

 

Clears the batch.

## Syntax

``` c++
  
HRESULT IBTTransportBatch::Clear(  
);  
  
```

``` vb
  
Sub Clear
()  
  
```

## Remarks

**Parameters**

None.

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


**Remarks**

This method is implicitly called when the [Done](ibttransportbatch-done-method-com.md) method is called.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportBatch Interface (COM)](ibttransportbatch-interface-com.md)  
[IBTTransportBatch Members (COM)](ibttransportbatch-members-com.md)

