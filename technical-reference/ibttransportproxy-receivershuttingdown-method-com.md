---
description: "Learn more about: IBTTransportProxy.ReceiverShuttingdown Method (COM)"
title: IBTTransportProxy.ReceiverShuttingdown Method (COM)
TOCTitle: IBTTransportProxy.ReceiverShuttingdown Method (COM)
ms:assetid: 767e6a3a-bbd2-4c02-81bb-3b3ff5faa0be
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560862(v=BTS.80)
ms:contentKeyID: 51529004
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportProxy.ReceiverShuttingdown Method (COM)

 

Notifies the BizTalk Server Messaging Engine that the receiver adapter is shutting down one of its receive locations.

## Syntax

``` c++
  
        HRESULT IBTTransportProxy::ReceiverShuttingdown(  
        BSTR  
        bstrReceiveURL,  
HRESULTpErrorInfo);  
```

``` vb
  
        Sub ReceiverShuttingdown(  
        bstrReceiveURL  
         As String,  
pErrorInfo As HRESULT)  
```

## Remarks

**Parameters**

*bstrReceiveURL*  
\[in\] String that contains the receive URL that is shutting down.

*bstrReceiveURL*  
**String** that contains the receive URL that is shutting down.

*pErrorInfo*  
\[in\] The error that is causing the URL to shut down.

*pErrorInfo*  
The error that is causing the URL to shut down.

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

A receiver adapter can use this method to shutdown a receive endpoint or URL.

The receive endpoint will not be enabled automatically when service is restarted.

The adapter should not submit any new work after this method has been called.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportProxy Interface (COM)](ibttransportproxy-interface-com.md)  
[IBTTransportProxy Members (COM)](ibttransportproxy-members-com.md)

