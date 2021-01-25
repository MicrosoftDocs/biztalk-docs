---
description: "Learn more about: IBTTransportProxy.TerminateIsolatedReceive Method (COM)"
title: IBTTransportProxy.TerminateIsolatedReceive Method (COM)
TOCTitle: IBTTransportProxy.TerminateIsolatedReceive Method (COM)
ms:assetid: 0a894785-8bb0-4a5f-afab-b85cc18ced67
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547233(v=BTS.80)
ms:contentKeyID: 51526099
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportProxy.TerminateIsolatedReceive Method (COM)

 

Notifies the Messaging Engine that it is shutting down. This method is called by a non-creatable receiver.

## Syntax

``` c++
  
HRESULT IBTTransportProxy::TerminateIsolatedReceiver();  
  
```

``` vb
  
Sub TerminateIsolatedReceiver
()  
  
```

## Remarks

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
</tbody>
</table>


**Remarks**

The **TerminateIsolatedReceiver** method should be called after all [RegisterIsolatedReceiver](ibttransportproxy-registerisolatedreceiver-method-com.md) method calls, the process will hang on exit if this is not done.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportProxy Interface (COM)](ibttransportproxy-interface-com.md)  
[IBTTransportProxy Members (COM)](ibttransportproxy-members-com.md)

