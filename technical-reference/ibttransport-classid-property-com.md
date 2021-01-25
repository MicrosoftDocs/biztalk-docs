---
description: "Learn more about: IBTTransport.ClassID Property (COM)"
title: IBTTransport.ClassID Property (COM)
TOCTitle: IBTTransport.ClassID Property (COM)
ms:assetid: 3de411ae-57e4-4af3-994d-0e8d26d735bf
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559724(v=BTS.80)
ms:contentKeyID: 51527469
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransport.ClassID Property (COM)

 

Gets the class ID of the adapter, a globally unique identifier (GUID) that identifies the adapter.

``` c++
  
ClassID  
  
```

``` vb
  
GUID  
```

## Remarks

**Parameters**

*ClassID*  
\[out, retval\] Globally unique identifier (GUID) used to return the class ID of the adapter.

None.

**Return Values**

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

Not applicable.

**Error Values**

This method returns an HRESULT containing one of the values in the following table.

This property indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.

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
<td>The property was successfully obtained or written.</td>
</tr>
</tbody>
</table>


**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransport Interface (COM)](ibttransport-interface-com.md)  
[IBTTransport Members (COM)](ibttransport-members-com.md)

