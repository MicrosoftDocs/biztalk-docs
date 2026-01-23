---
description: "Learn more about: IBTTransport.TransportType Property (COM)"
title: IBTTransport.TransportType Property (COM)
TOCTitle: IBTTransport.TransportType Property (COM)
ms.topic: reference
ms:assetid: 9d676d74-89dd-41ed-8ee3-81e9f34fa88e
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577583(v=BTS.80)
ms:contentKeyID: 51530024
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransport.TransportType Property (COM)

 

Gets the transport type of an adapter, such as FILE, HTTP, SMTP, or SOAP.

``` c++
  
TransportType  
  
```

``` vb
```

## Remarks

**Parameters**

*TransportType*  
\[out,retval\] String used to return the name of the protocol implemented by the adapter.

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

