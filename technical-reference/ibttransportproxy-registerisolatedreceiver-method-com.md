---
description: "Learn more about: IBTTransportProxy.RegisterIsolatedReceiver Method (COM)"
title: IBTTransportProxy.RegisterIsolatedReceiver Method (COM)
TOCTitle: IBTTransportProxy.RegisterIsolatedReceiver Method (COM)
ms:assetid: 589f7158-8a05-4522-9bc2-07ba2f9b197c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560283(v=BTS.80)
ms:contentKeyID: 51528199
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IBTTransportProxy.RegisterIsolatedReceiver Method (COM)

 

Registers an isolated receiver.

## Syntax

``` c++
  
        HRESULT IBTTransportProxy::RegisterIsolatedReceiver(  
        BSTR  
        bstrURL,  
IBTTransportConfig*pCallBack);  
```

``` vb
  
        Sub RegisterIsolatedReceiver(  
        bstrURL  
         As String,  
pCallBack As IBTTransportConfig)  
```

## Remarks

**Parameters**

*bstrURL*  
\[in\] String that contains the URL that the adapter is listening on.

*bstrURL*  
**String** that contains the URL that the adapter is listening on.

*pCallBack*  
\[in\] Reference to a **IBTTransportConfig** object/interface that will be called back with the configuration of the *bstrURL* parameter.

*pCallBack*  
**IBTTransportConfig** object/interface that will be called back with the configuration of the *bstrURL* parameter.

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

An ISAPI extension is an example of a non-creatable receive function because BizTalk Server does not have control over the lifetime of the ISAPI extension. In this scenario, the non-creatable adapter is responsible for creating the transport proxy and registering itself with the transport proxy.

The [TerminateIsolatedReceive](ibttransportproxy-terminateisolatedreceive-method-com.md)method should be called after all **RegisterIsolatedReceiver** method calls, the process will hang on exit if this is not done.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportProxy Interface (COM)](ibttransportproxy-interface-com.md)  
[IBTTransportProxy Members (COM)](ibttransportproxy-members-com.md)

