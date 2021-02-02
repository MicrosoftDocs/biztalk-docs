---
description: "Learn more about: IBTTransportConfig.AddReceiveEndpoint Method (COM)"
title: IBTTransportConfig.AddReceiveEndpoint Method (COM)
TOCTitle: IBTTransportConfig.AddReceiveEndpoint Method (COM)
ms:assetid: d215daf8-c25b-4601-af3d-ded7cddde612
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578554(v=BTS.80)
ms:contentKeyID: 51531541
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportConfig.AddReceiveEndpoint Method (COM)

 

Adds a new URL address that the adapter should listen on for incoming messages.

## Syntax

``` c++
  
        HRESULT IBTTransportConfig::AddReceiveEndpoint(  
        BSTR  
        bstrURL,  
IPropertyBag*pConfig,  
IPropertyBag*pBizTalkConfig);  
```

``` vb
  
        Sub AddReceiveEndpoint(  
        bstrURL  
         As String,  
pConfig As IPropertyBag,  
pBizTalkConfig As IPropertyBag)  
```

## Remarks

**Parameters**

*bstrURL*  
\[in\] String that contains the URL the adapter should listen on.

*bstrURL*  
**String** that contains the URL the adapter should listen on.

*pConfig*  
\[in\] Reference to a **IPropertyBag** object/interface that contains the configuration for this URL.

*pConfig*  
**IPropertyBag** object/interface that contains the configuration for this URL.

*pBizTalkConfig*  
\[in\] Reference to a **IPropertyBag** object/interface that contains the BizTalk Server configuration, specifically the port capabilities that indicate whether the port is one way or two way. This is indicated by the property **TwoWayReceivePort**.

*pBizTalkConfig*  
**IPropertyBag** object/interface that contains the BizTalk Server configuration, specifically the port capabilities that indicate whether the port is one way or two way. This is indicated by the property **TwoWayReceivePort**.

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

This method is called by the BizTalk Server Messaging Engine.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportConfig Interface (COM)](ibttransportconfig-interface-com.md)  
[IBTTransportConfig Members (COM)](ibttransportconfig-members-com.md)

