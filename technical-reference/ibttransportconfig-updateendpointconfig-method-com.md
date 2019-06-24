---
title: IBTTransportConfig.UpdateEndpointConfig Method (COM)
TOCTitle: IBTTransportConfig.UpdateEndpointConfig Method (COM)
ms:assetid: cdb73a17-f39f-425c-8fd2-6a496f9717f9
ms:mtpsurl: https://msdn.microsoft.com/library/Aa548075(v=BTS.80)
ms:contentKeyID: 51531304
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportConfig.UpdateEndpointConfig Method (COM)

 

Updates the configuration of the URL.

## Syntax

``` c++
  
        HRESULT IBTTransportConfig::UpdateEndpointConfig(  
        BSTR  
        bstrURL,  
IPropertyBag*pConfig,  
IPropertyBag*pBizTalkConfig);  
```

``` vb
  
        Sub UpdateEndpointConfig(  
        bstrURL  
         As String,  
pConfig As IPropertyBag,  
pBizTalkConfig As IPropertyBag)  
```

## Remarks

**Parameters**

*bstrURL*  
\[in\] String that contains the URL that needs to be configured.

*bstrURL*  
**String** that contains the URL that needs to be configured.

*pConfig*  
\[in\] Reference to a **IPropertyBag** object/interface that contains the new configuration for the URL.

*pConfig*  
**IPropertyBag** object/interface that contains the new configuration for the URL.

*pBizTalkConfig*  
\[in\] Reference to a **IPropertyBag** object/interface that contains the BizTalk Server configuration, specifically the port capabilities, which indicate whether the port is one way or two way.

*pBizTalkConfig*  
**IPropertyBag** object/interface that contains the BizTalk Server configuration, specifically the port capabilities, which indicate whether the port is one way or two way.

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

